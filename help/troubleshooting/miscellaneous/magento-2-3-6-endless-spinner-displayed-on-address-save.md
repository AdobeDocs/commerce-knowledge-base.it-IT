---
title: "Adobe Commerce 2.3.6: rotazione continua visualizzata al salvataggio dell’indirizzo"
description: Questo articolo descrive un problema noto di Adobe Commerce 2.3.6, in cui lo spinner in attesa viene visualizzato indefinitamente quando si salva un indirizzo in Il mio account nella vetrina.
exl-id: 63841114-167e-4915-b6ed-ee0ef4eae36e
feature: Shipping/Delivery, Orders, Checkout
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# Adobe Commerce 2.3.6: rotazione continua visualizzata al salvataggio dell’indirizzo

Questo articolo descrive un problema noto di Adobe Commerce 2.3.6, in cui lo spinner in attesa viene visualizzato indefinitamente quando si salva un indirizzo in Il mio account nella vetrina.

## Prodotti e versioni interessati

* Adobe Commerce 2.3.6 con integrazione Vertex abilitata (solo browser Firefox)

## Problema

Quando salvi un indirizzo nella sezione Il mio account sulla vetrina, a volte lo spinner in attesa viene visualizzato indefinitamente a causa di un errore in Vertex core JS.

## Soluzione alternativa

Soluzione alternativa: utilizza un browser alternativo a Firefox.

Il problema è stato risolto in Adobe Commerce 2.3.1.

## Lettura correlata

* [Indirizzi diversi non consentiti quando si deseleziona &#39;Il mio indirizzo di fatturazione e spedizione è uguale&#39; utilizzando VertexAddress Cleansing](/help/troubleshooting/miscellaneous/vertex-address-cleansing-different-addresses-not-allowed.md) nella Knowledge Base del supporto tecnico.
* [Aggiornamento dell&#39;indirizzo di posta del messaggio di convalida degli indirizzi verticali di Adobe Commerce 2.4.1](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md) nella Knowledge Base del supporto tecnico.
