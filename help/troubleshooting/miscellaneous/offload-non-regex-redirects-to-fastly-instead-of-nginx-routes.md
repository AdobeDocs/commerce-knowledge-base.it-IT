---
title: 'Offload non-[!DNL regex] reindirizzamenti a [!DNL Fastly] invece di [!DNL Nginx] (route)'
description: In questo argomento viene suggerita una soluzione a un tipico problema di prestazioni che potrebbe verificarsi quando si scaricano reindirizzamenti non[!DNL regex] a [!DNL Fastly] invece di [!DNL Nginx] in Adobe Commerce sull'infrastruttura cloud.
exl-id: 8b22d25d-0865-4d21-b275-d344ba8748f2
feature: Routes
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '712'
ht-degree: 0%

---

# Offload non-[!DNL regex] reindirizzamenti a [!DNL Fastly] invece di [!DNL Nginx] (route)

In questo argomento viene suggerita una soluzione a un problema di prestazioni tipico dei reindirizzamenti che potrebbe verificarsi quando si scaricano reindirizzamenti non [!DNL regex] a [!DNL Fastly] invece di [!DNL Nginx] in Adobe Commerce sull&#39;infrastruttura cloud.

## Prodotti e versioni interessati

* Adobe Commerce sull&#39;infrastruttura cloud (tutte le versioni) `Master/Production/Staging` ambienti che sfruttano [!DNL Fastly]

## Problema

In Adobe Commerce sull&#39;infrastruttura cloud, un numero elevato di reindirizzamenti/riscritture non [!DNL regex] non può essere eseguito al livello [!DNL Nginx] e, di conseguenza, può causare problemi di prestazioni.

## Causa

Il file `routes.yaml` nella directory `.magento/routes.yaml` definisce le route per l&#39;infrastruttura cloud di Adobe Commerce.

Se la dimensione del file `routes.yaml` è pari o superiore a 32 KB, è necessario scaricare i reindirizzamenti/riscritture non [!DNL regex] in [!DNL Fastly].

Questo livello [!DNL Nginx] non può gestire un numero elevato di reindirizzamenti/riscritture non [!DNL regex], altrimenti si verificheranno problemi di prestazioni.

## Soluzione

La soluzione è quella di scaricare i reindirizzamenti non [!DNL regex] a [!DNL Fastly]. Creare un percorso di errore generico per reindirizzare a [!DNL Fastly].

Nei passaggi seguenti verrà descritto come inserire i reindirizzamenti in [!DNL Fastly] anziché in [!DNL Nginx].

1. Crea un dizionario Edge.

   È innanzitutto possibile utilizzare [[!DNL VCL] snippet in Adobe Commerce](/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html) per definire un dizionario perimetrale. Conterrà i reindirizzamenti.

   Alcune avvertenze:

   * [!DNL Fastly] non può fare [!DNL regex] sulle voci del dizionario. È solo una corrispondenza esatta. Per ulteriori informazioni su queste limitazioni, consulta la documentazione di [[!DNL Fastly] sulle limitazioni del dizionario Edge](https://docs.fastly.com/guides/edge-dictionaries/about-edge-dictionaries#limitations-and-considerations).
   * [!DNL Fastly] ha un limite di 1000 voci in un singolo dizionario. [!DNL Fastly] può espandere questo limite, ma questo comporta la terza avvertenza.
   * Ogni volta che aggiorni le voci e distribuisci che aggiorni [!DNL VCL] in tutti i nodi, si verifica un aumento geometrico del tempo di caricamento con i dizionari in espansione, il che significa che un dizionario di 2000 voci verrà caricato 3 volte e 4 volte più lentamente di un dizionario di 1000 voci. Ma questo è un problema solo quando distribuisci [!DNL VCL] (aggiornando il dizionario o modificando il codice della funzione [!DNL VCL]).

     Non influisce sul tempo necessario a [!DNL Fastly] per elaborare una richiesta; influisce solo sul tempo necessario a [!DNL Fastly] per inviare una nuova configurazione.

     In generale, i cambiamenti di configurazione richiedono in media alcuni secondi, di solito non più di 5-10 secondi. Pertanto, un aumento raddoppiato degli elementi del dizionario richiede fino a 30 secondi per implementare la configurazione. Un aumento di 4x richiederebbe meno di 2 minuti. Questo porta alla quarta avvertenza.

   * Esiste un limite piuttosto rigido di 10.000 voci in un dizionario Edge.

   Si consiglia vivamente di consolidare l’elenco dei reindirizzamenti. È possibile utilizzare più dizionari, ma qualsiasi aggiornamento apportato a [!DNL VCL] richiederà alcuni minuti per essere effettivamente popolato in [!DNL Fastly].

1. Confrontare [!DNL URL] con i dizionari.

   Quando si verifica la ricerca [!DNL URL], questo eseguirà il confronto per applicare il codice di errore personalizzato se viene trovata una corrispondenza.

   Utilizzare un altro frammento [!DNL VCL] per aggiungere qualcosa di simile al seguente a `vcl_recv`:

   ```
        declare local var.redir-path STRING;
        set var.redir-path = table.lookup(redirects, std.tolower(req.url), "");
   
        if (var.redir-path != "") {
          error 912 var.redir-path;
        }
   ```

   Qui stiamo verificando se [!DNL URL] esiste nella voce della tabella. In caso contrario, verrà chiamato un errore interno [!DNL Fastly] e verrà passato all&#39;errore il reindirizzamento [!DNL URL] dalla tabella.

1. Gestire il reindirizzamento.

   Quando viene trovata una corrispondenza, viene eseguita l&#39;azione definita per tale `obj.status`, in questo caso un reindirizzamento di spostamento permanente 301.

   Utilizzare uno snippet finale in `vcl_error` per inviare nuovamente i codici di errore 301 al client:

   ```
     if (obj.status == 912) {
        set obj.http.location = obj.response;
        set obj.status = 301;
        set obj.response = "Moved Permanently";
        return(deliver);
          }
   ```

   Con questo blocco, stiamo verificando se il codice di errore trasmesso da `vcl_recv` corrisponde e, in tal caso, imposteremo il percorso sul messaggio di errore trasmesso, quindi modificheremo il codice di stato in 301 e il messaggio in &quot;Spostato definitivamente&quot;. A questo punto, la risposta dovrebbe essere pronta per tornare al client.

### Servizio stage

>[!WARNING]
>
>Se desideri provare tutti questi passaggi, ti consigliamo vivamente di impostare un ambiente di staging Adobe Commerce. In questo modo è possibile eseguire test sul servizio [!DNL Fastly] per verificare che tutto si comporti come previsto.

Se non si desidera eseguire un ambiente di gestione temporanea di Adobe Commerce, ma si desidera verificare l&#39;aspetto di questi reindirizzamenti, è possibile impostare un account di gestione temporanea direttamente su [!DNL Fastly].

## Lettura correlata

* [[!DNL Fastly VCL] riferimento](https://docs.fastly.com/vcl/)
* [Configurare le route](/docs/commerce-cloud-service/user-guide/configure/routes/routes-yaml.html) nella documentazione per gli sviluppatori
* [Configurazione [!DNL Fastly]](/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) nella documentazione per gli sviluppatori
* [[!DNL VCL] scheda di riferimento rapido per espressioni regolari](https://docs.fastly.com/en/guides/vcl-regular-expression-cheat-sheet) nella documentazione per gli sviluppatori
* [Best practice per la modifica delle tabelle del database](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) nel playbook di implementazione di Commerce
