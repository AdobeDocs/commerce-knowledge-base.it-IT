---
title: Immagini di archivio non visualizzate dopo la distribuzione
description: Questo articolo fornisce una soluzione per i casi in cui le immagini non vengano visualizzate correttamente dopo la distribuzione.
exl-id: 7e6bcebd-edff-437a-9103-2743443d2ed9
feature: Cache, Categories, Deploy, Storefront
role: Admin
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%
---
# Immagini di archivio non visualizzate dopo la distribuzione

Questo articolo fornisce una soluzione per i casi in cui le immagini non vengano visualizzate correttamente dopo la distribuzione.

## Prodotti e versioni interessati

* Adobe Commerce sull’infrastruttura cloud 2.2.x, 2.3.x

## Problema

Quando si utilizza un tema vetrina con ridimensionamento immagine, le immagini non vengono visualizzate o scompaiono dalle pagine del catalogo durante la distribuzione.

## Causa

Ciò può verificarsi a causa del caricamento delle immagini dalla cache.

## Soluzione

In questo caso, puoi utilizzare il comando Magento per rigenerare la cache delle immagini e visualizzarle correttamente.

Per eseguire questa operazione, è necessario disporre delle informazioni SSH e dell&#39;URL dell&#39;archivio disponibili tramite [Cloud Console](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html).

1. SSH al progetto che era un&#39;origine per il [dump del database](/help/how-to/general/create-database-dump-on-cloud.md), come descritto in [SSH all&#39;ambiente](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections) nella documentazione per gli sviluppatori.
1. Rigenera la cache delle immagini eseguendo:

   ```bash
   php bin/magento catalog:images:resize
   ```

1. Verifica le pagine delle categorie tramite l’URL dello store.
