---
title: "La distribuzione non riesce se vengono utilizzate le chiavi di accesso corrette in env:COMPOSER_AUTH o auth.json"
description: 'Questo articolo fornisce una soluzione al problema che si verifica quando la distribuzione non riesce e viene visualizzato il seguente errore: "Impossibile scaricare il file https://repo.magento.com/archives/magento/module-customer-balance/magento-module-customer-balance-100.4.0.0.zip (HTTP/1.1 404 - Non trovato)".'
feature: Deploy
role: Admin
source-git-commit: 8e0aca8f528b017e288ae6fb19b072a5cc04761b
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# La distribuzione non riesce con le chiavi di accesso corrette in env:COMPOSER_AUTH o auth.json

Questo articolo fornisce una soluzione al problema che si verifica quando l’implementazione non riesce e viene visualizzato un errore simile a quello riportato di seguito, nel [registro di distribuzione](/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log):

```
W:   [Composer\Downloader\TransportException]
W:   The "https://repo.magento.com/archives/magento/module-customer-balance/magento-module-customer-balance-100.4.0.0.zip" file could not be downloaded (HTTP/1.1 404 Not Found)
```

## Prodotti e versioni interessati

Adobe Commerce sull’infrastruttura cloud 2.4.x

## Problema  

<u>Passaggi da riprodurre</u>:

Tentativo di distribuzione. 

<u>Risultati previsti</u>:

Distribuzione completata.

<u>Risultati effettivi</u>:

>[!NOTE]
>
>Questo è un errore di esempio. Potresti visualizzare un errore che indica un file diverso (a seconda della versione di Adobe Commerce implementata).

La distribuzione non è riuscita. Viene visualizzato un errore simile a *Impossibile scaricare il file &quot;https://repo.magento.com/archives/magento/module-customer-balance/magento-module-customer-balance-100.4.0.0.zip&quot; (HTTP/1.1 404 - Non trovato)* nel [registro di distribuzione](/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log).


### Causa

Le chiavi di accesso del compositore specificate presenti in una di queste posizioni potrebbero non avere accesso al codice:

* nel `env:COMPOSER_AUTH` variabile a livello di progetto
* nel `auth.json file`, che ha la precedenza rispetto al `env:COMPOSER_AUTH` variabile.

### Soluzione

Aggiornare il `env:COMPOSER_AUTH` a livello di progetto e assicurati che sia configurato con chiavi che hanno accesso al codice.

Per i passaggi, consulta [Livelli variabili](/docs/commerce-cloud-service/user-guide/configure/env/variable-levels) nella Guida all’infrastruttura cloud di Commerce.

## Lettura correlata

* [Impossibile accedere all’archivio Adobe Commerce sul cloud: errore 403 Forbidden o 404 Not Found durante la distribuzione](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html)
* [Errore di distribuzione: errore 7 durante il download della porta 443. Connessione rifiutata](/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/deployment-error-downloading-connection-refused-adobe-commerce.html)
