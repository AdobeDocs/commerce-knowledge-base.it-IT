---
title: Offload di reindirizzamenti non regex a Fastly anziché a Nginx (route)
description: Questo argomento suggerisce una soluzione a un tipico problema di prestazioni che si potrebbe avere quando si scaricano reindirizzamenti non regex a Fastly invece di Nginx in Adobe Commerce sull’infrastruttura cloud.
exl-id: 8b22d25d-0865-4d21-b275-d344ba8748f2
feature: Routes
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 0%

---

# Offload di reindirizzamenti non regex a Fastly anziché a Nginx (route)

Questo argomento suggerisce una soluzione a un tipico problema di prestazioni che si potrebbe avere quando si scaricano reindirizzamenti non regex a Fastly invece di Nginx in Adobe Commerce sull’infrastruttura cloud.

## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud (tutte le versioni) `Master/Production/Staging` ambienti che sfruttano Fastly

## Problema

Nell’infrastruttura cloud di Adobe Commerce on, non è possibile eseguire un numero elevato di reindirizzamenti/riscritture non regex a livello Nginx e, di conseguenza, può causare problemi di prestazioni.

## Causa

Il `routes.yaml` file in `.magento/routes.yaml` definisce le route per l’infrastruttura cloud di Adobe Commerce.

Se le dimensioni del `routes.yaml` è pari o superiore a 32 KB, è necessario scaricare i reindirizzamenti/riscritture non regex su Fastly.

Questo livello Nginx non può gestire un numero elevato di reindirizzamenti/riscritture non regex, altrimenti si verificheranno problemi di prestazioni.

## Soluzione

La soluzione è scaricare i reindirizzamenti non regex su Fastly. Crea un percorso di errore generico per reindirizzare a Fastly.

I passaggi seguenti spiegano come posizionare i reindirizzamenti su Fastly invece di Nginx.

1. Creare un dizionario Edge.

   Innanzitutto, puoi utilizzare [Snippet VCL in Adobe Commerce](/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html) per definire un dizionario edge. Conterrà i reindirizzamenti.

   Alcune avvertenze:

   * Fastly non può fare regex sulle voci del dizionario. È solo una corrispondenza esatta. Per ulteriori informazioni su queste limitazioni, consulta [Documenti di Fastly sulle limitazioni del dizionario Edge](https://docs.fastly.com/guides/edge-dictionaries/about-edge-dictionaries#limitations-and-considerations).
   * Fastly ha un limite di 1000 voci in un singolo dizionario. Fastly può espandere questo limite, ma questo porta alla terza avvertenza.
   * Ogni volta che aggiorni le voci e distribuisci quel VCL aggiornato a tutti i nodi, c&#39;è un aumento geometrico del tempo di caricamento con dizionari in espansione - il che significa, un dizionario di 2000 voci in realtà si carica 3x-4x più lentamente di un dizionario di 1000 voci. Ma questo è un problema solo quando distribuisci il VCL (aggiornando il dizionario o modificando il codice della funzione VCL).

     Non influisce sul tempo necessario a Fastly per elaborare una richiesta; influisce solo sul tempo necessario a Fastly per inviare una nuova configurazione.

     In generale, i cambiamenti di configurazione richiedono in media alcuni secondi, di solito non più di 5-10 secondi. Pertanto, un aumento raddoppiato degli elementi del dizionario richiede fino a 30 secondi per implementare la configurazione. Un aumento di 4x richiederebbe meno di 2 minuti. Questo porta alla quarta avvertenza.

   * Esiste un limite piuttosto rigido di 10.000 voci in un dizionario Edge.

   Si consiglia vivamente di consolidare l’elenco dei reindirizzamenti. Puoi utilizzare più dizionari, ma tieni presente che qualsiasi aggiornamento apportato al tuo VCL richiederà alcuni minuti per essere effettivamente popolato in Fastly.

1. Confronta l’URL con i dizionari.

   Quando si verifica la ricerca URL, viene eseguito il confronto per applicare il codice di errore personalizzato, se viene trovata una corrispondenza.

   Utilizzate un altro frammento VCL per aggiungere un elemento simile al seguente `vcl_recv`:

   ```
        declare local var.redir-path STRING;
        set var.redir-path = table.lookup(redirects, std.tolower(req.url), "");
   
        if (var.redir-path != "") {
          error 912 var.redir-path;
        }
   ```

   In questo caso, verifichiamo se l’URL esiste nella voce della tabella. In caso affermativo, verrà richiamato un errore Fastly interno e verrà trasmesso all’errore l’URL di reindirizzamento dalla tabella.

1. Gestire il reindirizzamento.

   Quando viene trovata una corrispondenza, viene eseguita l’azione definita per tale corrispondenza `obj.status`, in questo caso un reindirizzamento di spostamento permanente 301.

   Utilizzare uno snippet finale in `vcl_error` per inviare nuovamente i codici di errore 301 al client:

   ```
     if (obj.status == 912) {
        set obj.http.location = obj.response;
        set obj.status = 301;
        set obj.response = "Moved Permanently";
        return(deliver);
          }
   ```

   Con questo blocco, stiamo controllando se il codice di errore è stato trasmesso da `vcl_recv` corrisponde e, in tal caso, imposta la posizione sul messaggio di errore trasmesso, quindi modifica il codice di stato in 301 e il messaggio in &quot;Spostato definitivamente&quot;. A questo punto, la risposta dovrebbe essere pronta per tornare al client.

### Servizio stage

>[!WARNING]
>
>Se desideri provare tutti questi passaggi, ti consigliamo vivamente di impostare un ambiente di staging Adobe Commerce. In questo modo, puoi eseguire test sul servizio Fastly per verificare che tutto si comporti come previsto.

Se non desideri eseguire un ambiente di staging di Adobe Commerce, ma desideri vedere come apparirebbero questi reindirizzamenti, puoi impostare un account di staging direttamente su Fastly.

## Lettura correlata

* [Riferimento VCL Fastly](https://docs.fastly.com/vcl/)
* [Configurare le route](/docs/commerce-cloud-service/user-guide/configure/routes/routes-yaml.html) nella documentazione per gli sviluppatori.
* [Configura Fastly](/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) nella documentazione per gli sviluppatori.
* [Scheda di riferimento rapido per espressioni regolari VCL](https://docs.fastly.com/en/guides/vcl-regular-expression-cheat-sheet) nella documentazione per gli sviluppatori.
