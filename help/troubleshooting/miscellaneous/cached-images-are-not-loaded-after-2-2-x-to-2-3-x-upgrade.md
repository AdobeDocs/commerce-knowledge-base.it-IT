---
title: Le immagini nella cache non vengono caricate dopo l’aggiornamento da 2.2.X a 2.3.X
description: Questo articolo fornisce la soluzione al problema che impedisce la visualizzazione delle immagini memorizzate in cache dopo l’aggiornamento da Adobe Commerce sull’infrastruttura cloud da 2.2.X a 2.3.X.
exl-id: 3e6bd5aa-bd5d-4880-8b78-64f280647abe
feature: Cache, Upgrade
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---

# Le immagini nella cache non vengono caricate dopo l’aggiornamento da 2.2.X a 2.3.X

Questo articolo fornisce la soluzione al problema che impedisce la visualizzazione delle immagini memorizzate in cache dopo l’aggiornamento da Adobe Commerce sull’infrastruttura cloud da 2.2.X a 2.3.X.

## Versioni interessate:

* Adobe Commerce su infrastruttura cloud Pro plan architecture 2.2.X, 2.3.X

## Problema

Dopo l’aggiornamento di Adobe Commerce da 2.2.X a 2.3.X, le immagini del prodotto memorizzate in cache non sono disponibili e viene visualizzata una pagina 404.

Il problema è causato dalla configurazione Nginx non corretta impostata in `.magento.app.yaml`: `index.php` (o nessuno) viene utilizzato per il `"/media"` posizione invece di `passthru: /get.php`.

## Soluzione

1. Controlla il tuo `.magento.app.yaml` file di configurazione, in corrispondenza di `"/media"` posizione. La configurazione corretta è simile alla seguente:

   ```yaml
   "/media":
       root: "pub/media"
       allow: true
       scripts: false
       expires: 1y
       passthru: "/get.php"
   ```

1. Se `passthru` non è impostato su `"/get.php"` e `expires` non è impostato, effettua le seguenti operazioni.
1. Correggete il file di configurazione.
   * Pianificazione iniziale: correggi il file autonomamente e invia le modifiche.
   * Piano Pro:
   * Integrazione: correggi il file autonomamente e invia le modifiche.
   * Staging e produzione: correggi il file, invia le modifiche e crea un [Ticket di supporto Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) per farla applicare.

1. Abilitare l’ottimizzazione Fastly delle immagini in Commerce Admin (Fastly deve essere configurato prima), come descritto in <https://devdocs.magento.com/guides/v2.3/cloud/cdn/fastly-image-optimization.html>.

Se la configurazione è corretta, ma il problema persiste, continua l’indagine o contatta [Supporto Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
