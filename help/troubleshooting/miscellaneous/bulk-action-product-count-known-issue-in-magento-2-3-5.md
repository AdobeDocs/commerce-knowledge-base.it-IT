---
title: Problema noto relativo al conteggio dei prodotti per azioni in blocco in Adobe Commerce 2.3.5
description: Questo articolo descrive un problema noto di Adobe Commerce 2.3.5, in cui la notifica che un esercente riceve dopo un’azione in blocco in Admin contiene un numero errato di elementi interessati.
exl-id: 3ede15d4-4c39-442a-8784-2d5e6650fe67
feature: Products
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# Problema noto relativo al conteggio dei prodotti per azioni in blocco in Adobe Commerce 2.3.5

Questo articolo descrive un problema noto di Adobe Commerce 2.3.5, in cui la notifica che un esercente riceve dopo un’azione in blocco in Admin contiene un numero errato di elementi interessati.

## Prodotti e versioni interessati

* Adobe Commerce sull’infrastruttura cloud 2.3.5
* Adobe Commerce on-premise 2.3.5

## Problema

Il messaggio di sistema visualizzato da Adobe Commerce dopo un’azione in blocco (ad esempio, un aggiornamento di massa del prodotto o un’importazione/esportazione) visualizza un conteggio pari a 0 invece di un conteggio accurato dei prodotti interessati dall’azione in blocco.

## Correzione

Una correzione sarà disponibile in Adobe Commerce 2.3.6, il cui rilascio è pianificato per il quarto trimestre del 2020.

## Lettura correlata

* Articoli della Knowledge Base di supporto Adobe Commerce per i problemi noti di Adobe Commerce 2.3.5:
   * [Ordini con spedizione multipla con un prodotto virtuale non elaborati correttamente in Adobe Commerce 2.3.5](/help/troubleshooting/miscellaneous/magento-2-3-5-known-issue-virtual-product-multi-ship-orders.md)
   * [Problema noto relativo al confronto dei prodotti in Adobe Commerce 2.3.5](/help/troubleshooting/storefront/product-comparison-known-issue-in-magento-2-3-5.md)
   * [Problema del metodo di pagamento nazionale in Adobe Commerce sull’infrastruttura cloud e Adobe Commerce on-premise 2.3.5 e 2.3.5-p1](/help/troubleshooting/known-issues-patches-attached/magento-2-3-5-2-3-5-p1-patch-country-payment-issue.md)
   * [Adobe Commerce richiede ai clienti di effettuare l’accesso ma fornisce un collegamento non valido](/help/troubleshooting/known-issues-patches-attached/magento-prompts-customers-log-in-invalid-link.md)
   * [Patch per il problema di pagamento Amazon in Adobe Commerce 2.3.5-p1](/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md)
   * [Problemi noti di Adobe Commerce 2.3.5 nella documentazione per gli sviluppatori](https://devdocs.magento.com/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues)
