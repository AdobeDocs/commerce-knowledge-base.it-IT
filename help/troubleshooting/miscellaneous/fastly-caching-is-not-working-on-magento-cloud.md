---
title: Il caching rapido non funziona su Adobe Commerce nell’infrastruttura cloud
description: Questo articolo fornisce una correzione per il mancato funzionamento del caching Fastly sul sito. Fastly è un servizio CDN e di caching incluso con Adobe Commerce sui piani e le implementazioni dell’infrastruttura cloud. Per verificare che l’estensione Fastly funzioni o per eseguire il debug dell’estensione Fastly, puoi utilizzare il comando curl per visualizzare determinate intestazioni di risposta. I valori di queste intestazioni di risposta indicano se Fastly è abilitato e funziona correttamente. Puoi analizzare ulteriormente i problemi in base ai valori delle intestazioni e al comportamento di caching.
exl-id: 725949e9-b69b-456f-9c56-e2163143a71e
feature: Cache, Cloud, Console, Paas
role: Developer
source-git-commit: 586a8c6340bfd2cbf773d1b009d6e106e930117d
workflow-type: tm+mt
source-wordcount: '1207'
ht-degree: 0%

---

# Il caching rapido non funziona su Adobe Commerce nell’infrastruttura cloud

Questo articolo fornisce una correzione per il mancato funzionamento del caching Fastly sul sito. Fastly è un servizio CDN e di caching incluso con Adobe Commerce sui piani e le implementazioni dell’infrastruttura cloud. Per verificare che l’estensione Fastly funzioni o per eseguire il debug dell’estensione Fastly, puoi utilizzare il comando curl per visualizzare determinate intestazioni di risposta. I valori di queste intestazioni di risposta indicano se Fastly è abilitato e funziona correttamente. Puoi analizzare ulteriormente i problemi in base ai valori delle intestazioni e al comportamento di caching.

Queste informazioni sono utili per verificare e testare le intestazioni Fastly per il sito live e i server di origine.

## Versioni interessate

* Adobe Commerce sull’infrastruttura cloud
* 1.2.27 e versioni successive

## Problema

La memorizzazione in cache potrebbe non funzionare per gli ambienti di sito live, produzione o staging.

## Causa

In genere, configurazioni, credenziali errate o estensioni Adobe Commerce non supportate causano il mancato funzionamento del caching Fastly. Se imposti Fastly in modo errato o utilizzi un’estensione non supportata che elimina le intestazioni, il caching Fastly non funzionerà.

## Test con comandi e verifica intestazioni di risposta

### Test con comando dig

Innanzitutto, controlla le intestazioni con un comando dig per l’URL. In un&#39;applicazione terminale, immettere dig `<url>` per verificare che i servizi Fastly vengano visualizzati nelle intestazioni. Per ulteriori test di analisi, consulta Fastly [Test prima della modifica del DNS](https://docs.fastly.com/guides/basic-configuration/testing-setup-before-changing-domains).

Ad esempio:

* Sito live: `dig http[s]://<your domain>`
* Staging: `dig http[s]://staging.<your domain>.c.<instanceid>.ent.magento.cloud`
* Produzione: `dig http[s]://<your domain>.{1|2|3}.<project ID>.ent.magento.cloud`

### Test con comando curl

Quindi, utilizza un comando curl per verificare l’esistenza di X-Magento-Tags e ulteriori informazioni sull’intestazione. Il formato del comando è diverso per Staging e Produzione.

Per ulteriori informazioni su questi comandi, ignorate Fastly durante l&#39;inserimento `-H "host:URL"`, sostituire con origine alla posizione di connessione (informazioni CNAME dal foglio di calcolo di OneDrive), `-k` ignora SSL e `-v` fornisce risposte dettagliate. Se le intestazioni vengono visualizzate correttamente, controlla il sito live e verifica di nuovo le intestazioni.

* Se si verificano problemi di intestazione quando si colpiscono direttamente i server di origine bypassando Fastly, è possibile che si verifichino problemi nel codice, con le estensioni o con l’infrastruttura.
* Se non si verificano errori quando si collegano direttamente i server di origine, ma nelle intestazioni manca il dominio live tramite Fastly, è possibile che si verifichino errori Fastly.

Per prima cosa, controlla **sito live** per verificare le intestazioni di risposta. Il comando passa attraverso l’estensione Fastly per ricevere le risposte. Se non ricevi le intestazioni corrette, devi testare direttamente i server di origine. Questo comando restituisce i valori del `Fastly-Magento-VCL-Uploaded` e `X-Cache` intestazioni.

1. In un terminale, immetti il seguente comando per verificare l’URL live del sito:

   ```
   curl http://<live URL> -vo /dev/null -HFastly-Debug:1 [--resolve]
   ```

   Utilizzare `--resolve` solo se l’URL live non è configurato con DNS e non è stata impostata una route statica. Ad esempio:

   ```
   curl http://www.mymagento.biz -vo /dev/null -HFastly-Debug:1
   ```

1. Verifica le intestazioni di risposta per assicurarti che Fastly funzioni. L’output di questo comando è simile a Curl Staging and Production. Ad esempio, dovresti visualizzare le intestazioni univoche restituite da questo comando:

   ```
   < Fastly-Magento-VCL-Uploaded: yes    < X-Cache: HIT, MISS
   ```

Da testare **Staging** :

```
curl http[s]://staging.<your domain>.c.<instanceid>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

Da testare **Load balancer di produzione** :

```
curl http[s]://<your domain>.c.<project ID>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

Da testare **Nodo di origine produzione** :

```
curl http[s]://<your domain>.{1|2|3}.<project ID>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

Un nodo di origine diretto:

```
curl http[s]://<your domain>.{1|2|3}.<project ID>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

Ad esempio, se disponi di un URL pubblico www.mymagento.biz, immetti un comando simile al seguente per testare il sito di produzione:

```
curl -k https://www.mymagento.biz.c.sv7gVom4qrpek.ent.magento.cloud -H 'Host: www.mymagento.biz' -vo /dev/null -HFastly-Debug:1
```

### Controllare le intestazioni di risposta

* Controlla le intestazioni e i valori di risposta restituiti:
* Deve essere presente Fastly-Magento-VCL-Uploaded
* I tag X-Magento devono essere restituiti
* Fastly-Module-Enabled deve essere impostato su Sì o sul numero di versione dell’estensione Fastly
* X-Cache deve essere HIT o HIT, HIT
* x-cache-hits deve essere 1,1
* Cache-Control: max-age deve essere maggiore di 0
* Pragma deve essere memorizzato nella cache

Nell&#39;esempio seguente vengono illustrati i valori corretti per Pragma, X-Magento-Tags e Fastly-Module-Enabled.

L&#39;output dei comandi curl può essere lungo. Di seguito è riportato solo un riepilogo:

```
* STATE: INIT => CONNECT handle 0x600057800; line 1402 (connection #-5000)
* Rebuilt URL to: https://www.mymagento.biz.c.sv7gVom4qrpek.ent.magento.cloud/
* Added connection 0. The cache now contains 1 members
* Trying 192.0.2.31...
* STATE: CONNECT => WAITCONNECT handle 0x600057800; line 1455 (connection #0)
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                             Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0* Connected to www.mymagento.biz.c.sv7gVom4qrpek.ent.magento.cloud (54.229.163.31) port 443 (#0)
* STATE: WAITCONNECT => SENDPROTOCONNECT handle 0x600057800; line 1562 (connection #0)
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0* ALPN, offering h2

  ... portion omitted for brevity ...

< Set-Cookie: mage-messages=%5B%5D; expires=Wed, 22-Nov-2017 17:39:58 GMT; Max-Age=31536000; path=/
< Pragma: cache
< Expires: Wed, 23 Nov 2016 17:39:56 GMT
< Cache-Control: max-age=86400, public, s-maxage=86400, stale-if-error=5, stale-while-revalidate=5
< X-Magento-Tags: cb_welcome_popup store cb cb_store_info_mobile cb_header_promotional_bar cb_store_info cb_discount-promo-bar cpg_2 cb_83 cb_81 cb_84 cb_85 cb_86 cb_87 cb_88 cb_89 p5646 catalog_product p5915 p6040 p6197 p6227 p7095 p6109 p6122 p6331 p7592 p7651 p7690
< Fastly-Module-Enabled: yes
< Strict-Transport-Security: max-age=31536000
    < Content-Security-Policy: upgrade-insecure-requests
< X-Content-Type-Options: nosniff
< X-XSS-Protection: 1; mode=block
< X-Frame-Options: SAMEORIGIN
< X-Platform-Server: i-dff64b52
<
* STATE: PERFORM => DONE handle 0x600057800; line 1955 (connection #0)
* multi_done
  0     0    0     0    0     0      0      0 --:--:--  0:00:02 --:--:--     0
* Connection #0 to host www.mymagento.biz.c.sv7gVom4qrpek.ent.magento.cloud left intact
```

## Risolvi

### Fastly-Module-Enabled non presente

Se non ricevi un &quot;sì&quot; per Fastly-Module-Enabled nelle intestazioni di risposta, devi verificare che il modulo Fastly sia installato e selezionato.

Per verificare che Fastly sia abilitato in Staging e Produzione, controlla la configurazione in Commerce Admin per ogni ambiente:

1. Accedi ad Admin Console per Staging e Produzione utilizzando l’URL con /admin (o l’URL Admin modificato).
1. Passa a Archivi > Configurazione > Avanzate > Sistema. Scorri e fai clic su Cache a pagina intera.
1. Assicurati che sia selezionato Fastly CDN.
1. Fai clic su Fastly Configuration. Assicurati di immettere l’ID servizio Fastly e il token API Fastly (le tue credenziali Fastly). Verifica di disporre delle credenziali corrette immesse per l’ambiente di staging e produzione. Fai clic su Verifica credenziali per ottenere assistenza.
1. Modifica il file compositore.json e assicurati che il modulo Fasty sia incluso nella versione. Questo file contiene tutti i moduli elencati con le versioni.

   * Nella sezione &quot;richiedi&quot;, è necessario disporre di &quot;fastly/magento2&quot;: `<version number>`
   * Nella sezione &quot;archivi&quot;, dovresti disporre di:

   ```
   "fastly-magento2": {    "type": "vcs",    "url": "https://github.com/fastly/fastly-magento2.git"    }
   ```

1. Se si utilizza Gestione configurazione, è necessario disporre di un file di configurazione. Modifica il file app/etc/config.app.php (2.0, 2.1) o app/etc/config.php (2.2) e assicurati che l’impostazione `'Fastly_Cdn' => 1` è corretta. L’impostazione non deve essere `'Fastly_Cdn' => 0` (disattivato).Se hai attivato Fastly, elimina il file di configurazione ed esegui il comando bin/magento magento-cloud:scd-dump per aggiornarlo. Per una descrizione di questo file, vedi [Esempio di gestione delle impostazioni specifiche del sistema](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/technical-details.html#manage-the-system-specific-configuration) nella Guida alla configurazione.

Se il modulo non è installato, è necessario installarlo in un [Ambiente di integrazione](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) e implementato in Staging e Produzione. Consulta [Configura Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) per istruzioni, consulta la Guida all’infrastruttura cloud di Commerce.

### Fastly-Magento-VCL-Uploaded non presente

Durante l’installazione e la configurazione, dovresti aver caricato Fastly VCL. Si tratta dei snippet VCL di base forniti dal modulo Fastly, non dei snippet VCL personalizzati creati. Per istruzioni, consulta [Carica snippet VCL Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#upload-vcl-to-fastly) nella Guida all’infrastruttura cloud di Commerce.

### X-Cache include MISS

Se X-Cache è impostato su HIT, MISS o MISS, MISS, immetti nuovamente lo stesso comando curl per assicurarti che la pagina non sia stata eliminata di recente dalla cache.

Se ottieni lo stesso risultato, utilizza i comandi curl e verifica le intestazioni di risposta:

* Pragma è cache
* X-Magento-Tags esiste
* Cache-Control: max-age è maggiore di 0

Se il problema persiste, è probabile che un’altra estensione ripristini queste intestazioni. Ripeti la seguente procedura in Staging per disabilitare le estensioni per trovare quella che sta causando il problema. Dopo aver individuato le estensioni che causano il problema, dovrai disabilitare le estensioni in Produzione.

1. Per disabilitare le estensioni, segui i passaggi indicati in [Gestire le estensioni](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/extensions.html?lang=en#manage-extensions) sezione della guida di Commerce sull’infrastruttura cloud.
1. Dopo aver disabilitato le estensioni, vai a **[!UICONTROL System]** > **[!UICONTROL Tools]** > **[!UICONTROL Cache Management]**.
1. Clic **[!UICONTROL Flush Magento Cache]**.
1. Ora abilita un’estensione alla volta, salvando la configurazione e svuotando la cache.
1. Prova i comandi curl e verifica le intestazioni di risposta.
1. Ripeti i passaggi 4 e 5 per abilitare e testare i comandi curl. Quando le intestazioni Fastly non vengono più visualizzate, è stato rilevato che l’estensione causava problemi con Fastly.

Quando isoli l’estensione che sta reimpostando le intestazioni Fastly, contatta lo sviluppatore dell’estensione per ulteriore assistenza. Non è possibile fornire correzioni o aggiornamenti affinché sviluppatori di estensioni di terze parti possano lavorare con il caching Fastly.

## Ulteriori informazioni sono disponibili nella documentazione per gli sviluppatori:

* [Informazioni su Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html)
* [Configura Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html)
* [Snippet VCL Fastly personalizzati](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html)
