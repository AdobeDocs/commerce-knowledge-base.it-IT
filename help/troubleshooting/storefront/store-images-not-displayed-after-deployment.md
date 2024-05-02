---
title: Immagini di archivio non visualizzate dopo la distribuzione
description: Questo articolo fornisce una soluzione per i casi in cui le immagini non vengano visualizzate correttamente dopo la distribuzione.
exl-id: 7e6bcebd-edff-437a-9103-2743443d2ed9
feature: Cache, Categories, Deploy, Storefront
role: Admin
source-git-commit: c4d586ca3980acbe4f33c5f2616ef7f3051bc7d3
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

Per eseguire questa operazione, è necessario disporre delle informazioni SSH e dell’URL dello store disponibili tramite [Console cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html).

1. SSH al progetto che è stato usato come origine per [dump del database](/help/how-to/general/create-database-dump-on-cloud.md), come descritto in [SSH nell’ambiente](https://devdocs.magento.com/guides/v2.3/cloud/env/environments-ssh.html#ssh) nella documentazione per gli sviluppatori.
1. Rigenera la cache delle immagini eseguendo:

   ```bash
   php bin/magento catalog:images:resize
   ```

1. Verifica le pagine delle categorie tramite l’URL dello store.
