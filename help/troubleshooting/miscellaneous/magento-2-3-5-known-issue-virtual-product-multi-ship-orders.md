---
title: "Problema noto di Adobe Commerce 2.3.5: ordini di prodotti virtuali con più spedizioni"
description: Questo articolo spiega un problema noto in Adobe Commerce 2.3.5 in cui un ordine di spedizione multipla contenente un prodotto virtuale non viene elaborato correttamente.
exl-id: 34ce79a2-5157-492b-8ee4-bdc09aae0c40
feature: Orders, Products, Shipping/Delivery
role: Developer
source-git-commit: b3d39e6b02728f05f046adf7be94ffacbca944d5
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---

# Problema noto di Adobe Commerce 2.3.5: ordini di prodotti virtuali con più spedizioni

Questo articolo spiega un problema noto in Adobe Commerce 2.3.5 in cui un ordine di spedizione multipla contenente un prodotto virtuale non viene elaborato correttamente.

## Prodotti e versioni interessati

* Adobe Commerce on-premise 2.3.5
* Adobe Commerce sull’infrastruttura cloud 2.3.5

## Problema

<u>Passaggi da riprodurre</u>:

1. Nella vetrina, aggiungi prodotti fisici e virtuali al carrello.
1. Procedi con l&#39;estrazione e seleziona **Estrai con più indirizzi**.
1. Aggiungi tutte le informazioni richieste e ordina.

<u>Risultato previsto</u>:

Gli ordini vengono effettuati correttamente per tutti i prodotti.

<u>Risultato effettivo</u>:

L&#39;ordine per il prodotto virtuale è vuoto.

## Correzione

Una correzione sarà disponibile in Adobe Commerce 2.3.6, il cui rilascio è pianificato per il quarto trimestre del 2020.

## Lettura correlata

Nella nostra knowledge base di supporto:

* [Problema noto relativo al confronto dei prodotti in Adobe Commerce 2.3.5](/help/troubleshooting/storefront/product-comparison-known-issue-in-magento-2-3-5.md)
* [Problema noto relativo al conteggio dei prodotti per azioni in blocco in Adobe Commerce 2.3.5](/help/troubleshooting/miscellaneous/bulk-action-product-count-known-issue-in-magento-2-3-5.md)
* [Patch per il problema di pagamento Amazon in Adobe Commerce 2.3.5-p1](/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md)

Nella documentazione per gli sviluppatori:

* [Note sulla versione di Adobe Commerce 2.3.5](https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues)
