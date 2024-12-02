---
title: 'Adobe Commerce su cloud: modifica le chiavi di autenticazione e ridistribuisci'
description: Questo articolo fornisce istruzioni su come ridistribuire Adobe Commerce su un’infrastruttura cloud con diverse chiavi di autenticazione. Ad esempio, potresti aver utilizzato le chiavi per un altro account o potresti aver utilizzato le chiavi di Magento Open Source invece delle chiavi di Adobe Commerce.
exl-id: 47407c81-5c52-406f-812f-6c6b3ca5cafa
feature: Cloud, Deploy
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Adobe Commerce su cloud: modifica le chiavi di autenticazione e ridistribuisci

Questo articolo fornisce istruzioni su come ridistribuire Adobe Commerce su un’infrastruttura cloud con diverse chiavi di autenticazione. Ad esempio, potresti aver utilizzato le chiavi per un altro account o potresti aver utilizzato le chiavi di Magento Open Source invece delle chiavi di Adobe Commerce.

Se sono state utilizzate chiavi non corrette, la distribuzione non riesce. Per ripristinare, è necessario clonare il progetto, aggiungere le chiavi corrette a `auth.json` e inviare la modifica al ramo principale.

In questo articolo, si presuppone che il progetto abbia solo un ramo `master` (`master` è il ramo predefinito al momento della creazione di un progetto).

Per ridistribuire con le chiavi di autenticazione corrette:

1. Accedi al computer in cui è installato Adobe Commerce sulle chiavi SSH dell’infrastruttura cloud.
1. Accedi al progetto:

   ```
   magento-cloud login
   ```

1. Creare un ramo per aggiornare il codice con il nome `auth`:

   ```
   magento-cloud environment:branch auth master
   ```

1. Passa alla directory principale del progetto.
1. Apri `auth.json` in un editor di testo.

   ```json
   {
      "http-basic": {
         "repo.magento.com": {
            "username": "<your public key>",
            "password": "<your private key>"
         }
      }
   }
   ```

1. Aggiungi le chiavi di autenticazione corrette.
1. Salva le modifiche e esci dall’editor di testo.
1. Eseguire il commit e unire le modifiche.

   ```
   git add -A
   ```

   ```
   git commit -m "<description of change>"
   ```

   ```
   git push origin master
   ```

1. Attendere il completamento della distribuzione.

I messaggi indicano se la distribuzione è stata eseguita correttamente. Puoi confermare la corretta distribuzione visitando una delle **route di ambiente** visualizzate sullo schermo.
