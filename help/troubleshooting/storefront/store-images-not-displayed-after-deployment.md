---
title: Immagini di archivio non visualizzate dopo la distribuzione
description: Questo articolo fornisce una soluzione per i casi in cui le immagini non vengano visualizzate correttamente dopo la distribuzione.
exl-id: 7e6bcebd-edff-437a-9103-2743443d2ed9
feature: Cache, Categories, Deploy, Storefront
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '162'
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

In questo caso, potete utilizzare il comando di Magento per rigenerare la cache delle immagini e visualizzarle correttamente.

Per eseguire questa operazione, è necessario disporre delle informazioni SSH e dell&#39;URL dell&#39;archivio disponibili tramite [Cloud Console](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=it).

1. SSH al progetto che era un&#39;origine per il [dump del database](/help/how-to/general/create-database-dump-on-cloud.md), come descritto in [SSH all&#39;ambiente](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/secure-connections) nella documentazione per gli sviluppatori.
1. Rigenera la cache delle immagini eseguendo:

   ```bash
   php bin/magento catalog:images:resize
   ```

1. Verifica le pagine delle categorie tramite l’URL dello store.
