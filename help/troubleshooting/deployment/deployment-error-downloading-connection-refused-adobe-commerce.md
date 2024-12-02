---
title: 'Errore di distribuzione: *errore 7 durante il download ... porta 443: connessione rifiutata*'
description: 'Questo articolo fornisce una soluzione per l’errore di distribuzione: *"errore 7 durante il download di ... porta 443: connessione rifiutata"*.'
exl-id: 520cf50f-3682-441d-87a7-8e05301a2b0c
feature: Cache, Deploy
role: Developer
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---

# Errore di distribuzione: *errore 7 durante il download della porta 443. Connessione rifiutata*

Questo articolo fornisce una correzione del problema quando la distribuzione non riesce con il seguente messaggio di errore:

```bash
W: In CurlDownloader.php line 370:
W:
W:   curl error 7 while downloading https://repo.packagist.org/p2/magento/module
W:   -sitemap.json: Failed to connect to repo.packagist.org port 443: Connection
W:    refused
```

## Versioni interessate

Adobe Commerce sull&#39;infrastruttura cloud, [tutte le versioni supportate](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problema

La distribuzione non riesce con un messaggio di errore **curl 7**.

<u>Passaggi da riprodurre</u>:

Attivare una distribuzione.

<u>Comportamento previsto</u>:

Implementazione completata.

<u>Comportamento effettivo</u>:

La distribuzione non riesce e nel registro di distribuzione viene visualizzato il seguente errore: *curl errore 7 durante il download della porta 443: Connessione rifiutata*.

## Causa

Ciò potrebbe essere dovuto alla perdita della connessione della cache all’archivio.

## Soluzione

Chiedi a un utente privilegiato sul progetto di eseguire questo comando:

```bash
magento-cloud project:clear-build-cache -p <project ID>
```

Per verificare chi è un utente privilegiato nel progetto, consulta [Visualizzare il ruolo di progetto di un utente](/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=en#view-a-user’s-project-role) nella Guida all&#39;infrastruttura di Commerce su Cloud.

## Lettura consigliata

* [Risoluzione dei problemi di distribuzione di Adobe Commerce](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-deployment-troubleshooter.html).
* [Impossibile accedere all&#39;archivio Adobe Commerce sul cloud: errore 403 Non consentito o 404 Non trovato durante la distribuzione](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html).
* [La distribuzione non riesce e viene visualizzato il messaggio &quot;Errore durante la compilazione del progetto: hook di compilazione non riuscito con codice di stato 1&quot;](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/deployment-fails-with-error-building-project-the-build-hook-failed-with-status-code-1.html).
