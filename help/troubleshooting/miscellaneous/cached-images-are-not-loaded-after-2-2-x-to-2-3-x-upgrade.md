---
title: Le immagini nella cache non vengono caricate dopo l’aggiornamento da 2.2.X a 2.3.X
description: Questo articolo fornisce la soluzione al problema che impedisce la visualizzazione delle immagini memorizzate in cache dopo l’aggiornamento da Adobe Commerce sull’infrastruttura cloud da 2.2.X a 2.3.X.
exl-id: 3e6bd5aa-bd5d-4880-8b78-64f280647abe
feature: Cache, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%
---
# Le immagini nella cache non vengono caricate dopo l’aggiornamento da 2.2.X a 2.3.X

Questo articolo fornisce la soluzione al problema che impedisce la visualizzazione delle immagini memorizzate in cache dopo l’aggiornamento da Adobe Commerce sull’infrastruttura cloud da 2.2.X a 2.3.X.

## Versioni interessate:

* Adobe Commerce su infrastruttura cloud Pro plan architecture 2.2.X, 2.3.X

## Problema

Dopo l’aggiornamento di Adobe Commerce da 2.2.X a 2.3.X, le immagini del prodotto memorizzate in cache non sono disponibili e viene visualizzata una pagina 404.

Il problema è causato dal set di configurazione Nginx non corretto in `.magento.app.yaml`: `index.php` (o nessuno) è utilizzato per il percorso `"/media"` invece di `passthru: /get.php`.

## Soluzione

1. Controllare il file di configurazione `.magento.app.yaml`, nel percorso `"/media"`. La configurazione corretta è simile alla seguente:

   ```yaml
   "/media":
       root: "pub/media"
       allow: true
       scripts: false
       expires: 1y
       passthru: "/get.php"
   ```

1. Se `passthru` non è impostato su `"/get.php"` e `expires` non è impostato, procedere come segue.
1. Correggete il file di configurazione.
   * Pianificazione iniziale: correggi il file autonomamente e invia le modifiche.
   * Piano Pro:
   * Integrazione: correggi il file autonomamente e invia le modifiche.
   * Gestione temporanea e produzione: correggi il file, invia le modifiche e crea un [ticket di supporto Adobe Commerce](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide) per applicarlo.

1. Abilitare l&#39;ottimizzazione immagine Fastly in Commerce Admin (Fastly deve essere configurato prima), come descritto in <https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization>.

Se la configurazione è corretta, ma il problema persiste, continuare l&#39;indagine o contattare il [supporto Adobe Commerce](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide).
