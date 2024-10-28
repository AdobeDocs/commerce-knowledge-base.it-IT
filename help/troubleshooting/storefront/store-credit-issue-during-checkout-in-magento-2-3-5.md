---
title: Memorizza il problema del credito durante il pagamento in Adobe Commerce 2.3.5
description: Questo articolo fornisce una soluzione alternativa per il problema noto relativo al credito del negozio durante il pagamento in Adobe Commerce 2.3.5, in cui gli acquirenti ricevono errori durante il pagamento dopo aver selezionato e successivamente rimosso l’utilizzo del credito del negozio. Una correzione permanente sarà disponibile in Adobe Commerce 2.3.6.
exl-id: a0cca226-4d95-40b3-bd37-f13d28591366
feature: Checkout, Orders, Storefront
role: Admin
source-git-commit: d51fd4d7b064b8eea6cd3771af279b74a8bdec48
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---

# Memorizza il problema del credito durante il pagamento in Adobe Commerce 2.3.5

Questo articolo fornisce una soluzione alternativa per il problema noto relativo al credito del negozio durante il pagamento in Adobe Commerce 2.3.5, in cui gli acquirenti ricevono errori durante il pagamento dopo aver selezionato e successivamente rimosso l’utilizzo del credito del negozio. Una correzione permanente sarà disponibile in Adobe Commerce 2.3.6.

## Prodotti e versioni interessati

* Adobe Commerce on-premise 2.3.5
* Adobe Commerce sull’infrastruttura cloud 2.3.5

## Problema

<u>Passaggi da riprodurre</u>:

1. Il cliente aggiunge prodotti al carrello e procede al pagamento.
1. Cliente specifica il credito del punto vendita come metodo di pagamento.
1. Il cliente rimuove il credito del negozio e modifica il metodo di pagamento.
1. Il cliente procede attraverso il pagamento.

<u>Risultati previsti</u>:

Tutte le informazioni sull&#39;ordine vengono visualizzate correttamente.

<u>Risultati effettivi</u>:

Adobe Commerce genera un errore nella sezione Sintetico ordine della pagina Ordine.

## Soluzione

I clienti possono aggiornare la pagina Ordine e le informazioni contenute nel Riepilogo ordine verranno caricate correttamente. Una correzione sarà disponibile in Adobe Commerce 2.3.6, il cui rilascio è pianificato per il quarto trimestre del 2020.

## Lettura correlata

Articoli per problemi noti di Adobe Commerce 2.3.5 nella knowledge base di supporto:

* [Ordini con spedizione multipla con un prodotto virtuale non elaborati correttamente in Adobe Commerce 2.3.5](/help/troubleshooting/miscellaneous/magento-2-3-5-known-issue-virtual-product-multi-ship-orders.md)

* [Problema del metodo di pagamento nazionale in Adobe Commerce sull’infrastruttura cloud e Adobe Commerce on-premise 2.3.5 e 2.3.5-p1](/help/troubleshooting/known-issues-patches-attached/magento-2-3-5-2-3-5-p1-patch-country-payment-issue.md)


* [Problema noto relativo al conteggio dei prodotti per azioni in blocco in Adobe Commerce 2.3.5](/help/troubleshooting/miscellaneous/bulk-action-product-count-known-issue-in-magento-2-3-5.md)

* [Patch per il problema di pagamento Amazon in Adobe Commerce 2.3.5-p1](/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md)

* [Problema di confronto del prodotto in Adobe Commerce 2.3.5](/help/troubleshooting/storefront/product-comparison-known-issue-in-magento-2-3-5.md)

Nella documentazione per gli sviluppatori:

* [Problemi noti di Adobe Commerce 2.3.5](https://devdocs.magento.com/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues)
