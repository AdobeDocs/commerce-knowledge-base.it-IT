---
title: Adobe Commerce *post-implementazione ignorata perché la distribuzione non è riuscita* errore
description: "Questo articolo spiega come analizzare un errore di distribuzione: *La post-distribuzione viene ignorata perché la distribuzione non è riuscita*"
exl-id: cd0a3015-b7b9-442e-8ac1-89447ef12cd7
feature: Deploy
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---

# Adobe Commerce *post-distribuzione ignorata perché la distribuzione non è riuscita* errore

Questo articolo spiega come analizzare un errore di distribuzione: *La post-distribuzione viene ignorata perché la distribuzione non è riuscita* che si verifica durante la distribuzione in ambienti diversi, ad esempio l’aggiornamento.

## Prodotti e versioni interessati

Adobe Commerce sull’infrastruttura cloud [tutte le versioni supportate](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

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

Per ottenere la traccia degli errori per determinare la causa effettiva, SSH al server e controllare il file di registro `var/log/install_upgrade.log`.
