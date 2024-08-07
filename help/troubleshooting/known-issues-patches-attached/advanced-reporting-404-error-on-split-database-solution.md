---
title: Errore Advanced Reporting 404 nella soluzione di database suddiviso
description: Questo articolo fornisce una patch per gli utenti di Adobe Commerce 2.3.x con [split database solution](https://devdocs.magento.com/guides/v2.3/config-guide/multi-master/multi-master.html) che presentano un errore 404 quando tentano di utilizzare la funzione di reporting avanzato.
exl-id: b81d4ada-5f38-4882-bc5b-ab4ccd63fc5f
feature: Commerce Intelligence
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---

# Errore Advanced Reporting 404 nella soluzione di database suddiviso

In questo articolo viene fornita una patch per gli utenti di Adobe Commerce 2.3.x con la [soluzione di database split](https://devdocs.magento.com/guides/v2.3/config-guide/multi-master/multi-master.html) che genera un errore 404 quando si tenta di utilizzare la funzione di reporting avanzato.

## Prodotti e versioni interessati

Adobe Commerce 2.3.0 - 2.3.5-p1

## Problema

La patch risolve il problema relativo all&#39;utilizzo di un nome di connessione errato per la raccolta dei dati delle virgolette. A causa del nome di connessione errato utilizzato, i dati delle offerte non vengono inviati al Magento Business Intelligence (MBI) e non è possibile generare i rapporti.

## Soluzione

Applica la [patch](assets/MDVA-26831_EE_2.3.4_v1.composer.patch.zip) fornita in questo articolo.

## Patch

La patch è allegata a questo articolo. Per scaricarlo, fai clic sul seguente collegamento:

[MDVA-26831\_EE\_2.3.4\_v1.compositore.patch](assets/MDVA-26831_EE_2.3.4_v1.composer.patch.zip)

## Come applicare il cerotto

Decomprimere il file e seguire le istruzioni in [Come applicare una patch del compositore fornita dall&#39;Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md).
