---
title: Archiviazione dei file bassa; il caricamento di pagine specifiche è lento
description: Questo articolo fornisce una soluzione al problema dello spazio su disco insufficiente causato da immagini di grandi dimensioni e complesse.
exl-id: 640c8f0d-f714-4cc1-a401-9264cfaf8e37
feature: Storage, Observability
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---

# Archiviazione dei file bassa; il caricamento di pagine specifiche è lento

Questo articolo fornisce una soluzione al problema dello spazio su disco insufficiente causato da immagini di grandi dimensioni e complesse.

## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud, tutte le versioni supportate
* Adobe Commerce locale, tutte le versioni supportate
* Magento Open Source, tutte le versioni supportate

## Problema

Lo storage su disco ridotto e il caricamento lento delle pagine possono essere causati da immagini grandi e complesse che utilizzano grandi quantità di storage in `pub/media/catalog/products` e la condivisione dello spazio su disco tra staging e produzione (a meno che non venga eseguito il provisioning di un ambiente di staging dedicato).

## Causa

Le immagini non sono ottimizzate per bilanciare le prestazioni con la qualità di visualizzazione.

## Soluzione

Prima di caricare le immagini, ottimizzale e comprimerle per bilanciare le prestazioni con la qualità di visualizzazione. Questo consente di aumentare lo spazio e ridurre i tempi di caricamento delle pagine. I PNG offrono dimensioni più piccole per le immagini con grandi aree di colore uniforme. I JPEG danno dimensioni più piccole per tutto il resto. Utilizza la compressione più elevata (senza degradazioni evidenti). Di solito si tratta del 60-80%.

Utilizzare [Ottimizzazione rapida delle immagini](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization.html) per produrre immagini più efficienti.

## Lettura correlata

Per informazioni sulla gestione dello spazio su disco (se utilizzi Adobe Commerce su infrastrutture cloud) consulta [Gestione dello spazio su disco in Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html) nella Guida all’infrastruttura cloud di Commerce.
