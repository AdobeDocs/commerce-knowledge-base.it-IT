---
title: Il sito cloud è lento
description: Questo articolo fornisce consigli su come migliorare le prestazioni del sito Adobe Commerce sull’infrastruttura cloud in caso di carichi di traffico elevati e su come ridurre tale carico.
exl-id: 144df36b-6305-4e57-b813-46bbb0ddedda
feature: Cache, Categories, Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '1064'
ht-degree: 0%

---

# Il sito cloud è lento

Questo articolo fornisce consigli su come migliorare le prestazioni del sito Adobe Commerce sull’infrastruttura cloud in caso di carichi di traffico elevati e su come ridurre tale carico.

## Versioni e versioni interessate

* Adobe Commerce su infrastruttura cloud, tutte le versioni

## Problema

<u>Passaggi da riprodurre</u>

1. Visita il tuo negozio Adobe Commerce.
1. Sfogliare una pagina di categoria.
1. Aggiungi un prodotto al carrello.

<u>Risultato previsto</u>

Il sito è reattivo e l’aggiunta di un prodotto al carrello è rapida.

<u>Risultato effettivo</u>

Il sito è lento oppure le pagine delle categorie sono veloci, ma la pagina del carrello è lenta.

## Passaggi e soluzioni di debug

Effettua le seguenti operazioni per individuare il motivo del rallentamento delle prestazioni e correggerlo. È possibile cambiare il primo e il secondo passaggio, ma procedere al blocco degli IP solo se l’ottimizzazione delle impostazioni della cache non aiuta.

1. Controlla la frequenza di accessi alla cache per le pagine con traffico elevato e riduci la quantità di dati con aggiornamenti pesanti.
1. Controlla la frequenza di hit della cache del sito complessiva e verifica la configurazione generale di cache/Fastly.
1. Identifica i client web che causano il carico elevato del server e blocca gli IP che causano il carico elevato.

I paragrafi seguenti forniscono ulteriori dettagli per ciascun passaggio.

### Passaggio 1: verifica la frequenza di accessi alla cache per le pagine con traffico elevato

Il primo passo per risolvere un sito bloccato da un traffico pesante è garantire che le pagine con il traffico più pesante, come la pagina principale del negozio e le pagine delle categorie principali, siano memorizzate correttamente nella cache.

Puoi scoprire le percentuali di hit della cache per queste pagine esaminando il `X-Cache` Intestazioni HTTP che utilizzano cURL, come descritto in [Verifica della cache tramite cURL](https://docs.fastly.com/guides/debugging/checking-cache#using-curl) nella documentazione di Fastly. Oppure controlla le stesse intestazioni utilizzando la scheda rete nella barra degli strumenti per sviluppatori del browser web preferito.

In Fastly rispetta generalmente le intestazioni di risposta provenienti dall’applicazione; tuttavia, se le intestazioni sono tutte impostate su &quot;do not cache&quot; e per la pagina &quot;to expire in the previous&quot; (Scadenza passata), Fastly non può memorizzare la pagina nella cache.

>[!WARNING]
>
>Si noti che Fastly modifica le intestazioni di risposta, pertanto la verifica dell’URL principale con cURL o il browser web non mostra necessariamente quali intestazioni vengono emesse dall’applicazione. È comune per Fastly rispondere ai browser web con intestazioni &quot;senza cache&quot;, ma per l’applicazione web stessa per consentire il caching e per Fastly per memorizzare correttamente in cache l’elemento. Pertanto, le informazioni sulle intestazioni &quot;cache-control&quot; e &quot;pragma&quot; non saranno utili in questo caso.

#### Risoluzione dei problemi per le pagine con traffico elevato

Se la pagina indice ha un tasso di hit basso, puoi correggerlo riducendo la quantità di dati fortemente aggiornati presenti in tale pagina.

### Passaggio 2: verificare la frequenza di accessi alla cache del sito complessiva

Per verificare la frequenza di accessi alla cache complessiva:

1. [Ottieni credenziali rapide](http://devdocs.magento.com/guides/v2.3/cloud/cdn/configure-fastly.html#cloud-fastly-creds) per il tuo ambiente Adobe Commerce su infrastruttura cloud.
1. Esegui il seguente comando cURL Linux/macOS per controllare la percentuale di hit per il sito negli ultimi 30 minuti, sostituendo e con i valori delle credenziali Fastly:

   `curl -H "Fastly-Key: " https://api.fastly.com/stats/service//field/hit_ratio?by=minute | json_pp`

   Puoi anche verificare i tassi di hit storici nell’ultimo giorno o mese modificando l’opzione di query relativa all’intervallo di tempo da `?by=minute` a `?by=hour` o `?by=day`. Per ulteriori informazioni su come ottenere le statistiche Fastly della cache, consulta [Opzioni query](https://docs.fastly.com/api/stats#Query) nella documentazione di Fastly.

   Il `| json_pp` L’opzione stampa l’output di risposta JSON utilizzando `json_pp` utilità. Se ricevi un errore_&#39;json\_pp not found&#39;_, installa il `json_pp` o utilizzare un altro strumento della riga di comando per la stampa JSON. In alternativa, elimina il `| json_pp` ed eseguire di nuovo il comando. L’output della risposta JSON non è formattato, ma puoi eseguirlo tramite un’utilità di pulizia JSON per rimuoverlo.

Una frequenza di hit superiore a 0,90 o al 90% indica che la cache di pagina intera funziona.

Una percentuale di hit inferiore allo 0,85 o all’85% potrebbe indicare un problema di configurazione del sito, oppure potresti avere installata un’estensione di terze parti che non consente di memorizzare il contenuto nella cache.

#### Risoluzione dei problemi relativi alla frequenza di accessi alla cache complessiva

1. Utilizzando le statistiche della hit rate oraria e giornaliera, identifica quando la hit rate ha iniziato a diminuire. Se la frequenza di hit si riduce improvvisamente nello stesso momento in cui hai distribuito una modifica al sito, puoi provare a ripristinarla finché il carico del sito non si abbassa.
1. Controlla la configurazione in Admin di Commerce, in **Negozi** > **Configurazione** > Avanzate > **Sistema** > **Cache a pagina intera**. Assicurati che **TTL per contenuto pubblico** non è impostato su un valore troppo basso.
1. Assicurati di aver [ha caricato i snippet VCL](https://devdocs.magento.com/guides/v2.3/cloud/cdn/configure-fastly.html#upload-vcl-snippets).
1. Se utilizzi snippet VCL personalizzati, esegui il debug per l’utilizzo corretto delle azioni &quot;pass&quot; o &quot;pipe&quot;: devono essere utilizzati con attenzione e almeno con una condizione di qualche tipo. Per ulteriori suggerimenti, consulta [Snippet VCL Fastly personalizzati](https://devdocs.magento.com/guides/v2.3/cloud/cdn/cloud-vcl-custom-snippets.html) nella documentazione per gli sviluppatori.

### Passaggio 3: identificare i siti Web che causano il carico elevato del server

Per ottenere informazioni sugli indirizzi IP che accedono al tuo archivio Adobe Commerce, puoi utilizzare uno dei seguenti metodi.

* Controlla i registri di accesso HTTP tramite una sessione SSH.
* Contatta il supporto Adobe Commerce per richiedere un elenco di indirizzi IP che causano un carico pesante sul sito.

#### Controlla i registri di accesso HTTP

Per visualizzare il registro di accesso del sito, eseguire il comando seguente dall&#39;ambiente di sviluppo locale:

```bash
magento-cloud log access
```

Visualizza altre righe con il

```bash
--lines
```

, ad esempio:

```bash
magento-cloud log access --lines=500
```

Puoi visualizzare questo registro e verificare se una grande parte delle richieste proviene da un indirizzo IP specifico. Un altro modo consiste nell’utilizzare `awk` , `sort` e `uniq` per contare automaticamente gli indirizzi IP più frequenti nel registro, come indicato di seguito:

```bash
magento-cloud log access --lines 2000 | awk '{print $1}' | sort | uniq -c | sort
  -nr
```

Se il

```bash
magento-cloud log
```

non funziona, è possibile connettersi al server remoto con SSH e controllare il file di registro in `/var/log/access.log`

Dopo aver identificato gli indirizzi IP che causano un carico eccessivo del server, puoi bloccarli configurando un elenco Bloccati IP da nel pannello di amministrazione di Commerce, in **Negozi** > **Configurazione** > AVANZATE > **Sistema** > **Cache a pagina intera** > **Configurazione rapida** > **Blocco**.

Se non riesci ad accedere all’amministratore a causa di un carico pesante, puoi utilizzare l’API Fastly per impostare le regole di blocco:

1. Creare l’ACL come descritto in [Utilizzo delle ACL tramite l’API](https://docs.fastly.com/guides/access-control-lists/working-with-acls-using-the-api) Documento Fastly.
1. In `recv` crea uno snippet VCL con il seguente contenuto, avendo sostituito ACL\_NAME\_GOES\_HERE con il nome dell’ACL creato nel passaggio precedente:

   ```
   if( req.http.Fastly-Client-IP ~ ACL_NAME_GOES_HERE ) {
   error 403 "Forbidden";
   }
   ```

Per ulteriori informazioni sul blocco degli indirizzi IP, vedi [Guida rapida al modulo Adobe Commerce](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/BLOCKING.md) in GitHub.
