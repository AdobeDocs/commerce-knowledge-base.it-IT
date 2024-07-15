---
title: Errore durante l’abilitazione dell’ottimizzazione immagine in Adobe Commerce
description: Questo articolo fornisce una soluzione al problema che si verifica quando Fastly Image Optimization (IO) è disabilitato per impostazione predefinita con una notifica per contattare Fastly per abilitare l’ottimizzazione dell’immagine. Fastly Cloud Image Optimizer è un servizio di manipolazione e ottimizzazione delle immagini in tempo reale che consente di velocizzare la distribuzione di immagini ottimizzando la larghezza di banda.
exl-id: 7b64c786-3c74-4642-b0d0-15b5648163a0
feature: Observability
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 0%

---

# Errore durante l’abilitazione dell’ottimizzazione immagine in Adobe Commerce

Questo articolo fornisce una soluzione al problema che si verifica quando Fastly Image Optimization (IO) è disabilitato per impostazione predefinita con una notifica per contattare Fastly per abilitare l’ottimizzazione dell’immagine. Fastly Cloud Image Optimizer è un servizio di manipolazione e ottimizzazione delle immagini in tempo reale che consente di velocizzare la distribuzione di immagini ottimizzando la larghezza di banda.

## Prodotti e versioni interessati

* Adobe Commerce sull’infrastruttura cloud 2.2.x, 2.3.x

## Problema

Nella pagina Fastly Configuration, accanto al frammento di I/O Fastly, viene visualizzato lo stato Corrente: \_disabilitato \_con il seguente messaggio sottostante: Contattare il rappresentante commerciale o inviare un messaggio di posta elettronica a `support@fastly.com` per richiedere l&#39;attivazione dell&#39;ottimizzazione immagine per il servizio Fastly.

## Causa

Il sito potrebbe non essere ancora attivo. Esistono processi in atto per precaricare il sito quando viene attivato nel database Fastly.

## Soluzione

Crea un [ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) e richiedi ottimizzazione immagine.
