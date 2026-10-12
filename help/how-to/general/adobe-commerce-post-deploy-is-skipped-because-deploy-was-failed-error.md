---
title: Adobe Commerce *post-implementazione ignorata perché la distribuzione non è riuscita* errore
description: 'Questo articolo spiega come analizzare un errore di distribuzione: *La post-distribuzione viene ignorata perché la distribuzione non è riuscita*'
exl-id: cd0a3015-b7b9-442e-8ac1-89447ef12cd7
feature: Deploy
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%
---
# Adobe Commerce *post-distribuzione ignorato perché la distribuzione non è riuscita* errore

Questo articolo spiega come analizzare un errore di distribuzione: *La post-distribuzione viene ignorata perché la distribuzione non è riuscita*, che si verifica durante la distribuzione in ambienti diversi, ad esempio l&#39;aggiornamento.

## Prodotti e versioni interessati

Adobe Commerce sull&#39;infrastruttura cloud [tutte le versioni supportate](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problema

La distribuzione non riesce e restituisce un messaggio di errore generico, pertanto non è chiaro come risolvere l’errore.

## Causa

Indeterminato: la causa di questo messaggio di errore dipende dal codice e dal database distribuiti.

## Come analizzare l’errore di distribuzione

```
[20XX-XX-XX XX:XX:XX] DEBUG: Running step: is-deploy-failed
    W:
    W: In Processor.php line 129:
    W:
    [20XX-XX-XX XX:XX:XX] ERROR: [201] Post-deploy is skipped because deploy was failed.
    W:   Post-deploy is skipped because deploy was failed.
    W:
    W:
    W: In DeployFailed.php line 39:
    W:
    W:   Post-deploy is skipped because deploy was failed.
    W:
    W:
    W: post-deploy
    W:
```

Per ottenere la traccia degli errori per determinare la causa effettiva, SSH al server e controllare il file di log `var/log/install_upgrade.log`.
