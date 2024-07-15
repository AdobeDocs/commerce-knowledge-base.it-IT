---
title: Adobe Commerce richiede ai clienti di effettuare l’accesso a un collegamento non valido
description: L’articolo fornisce un collegamento alla patch per un problema noto di Adobe Commerce 2.3.5, in cui ai clienti viene richiesto di effettuare l’accesso, ma il collegamento per inviare nuovamente un’e-mail di conferma non funziona.
exl-id: 8adef44f-56a6-4f57-a9b5-fb8583d8ae8d
feature: Logs
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---

# Adobe Commerce richiede ai clienti di effettuare l’accesso a un collegamento non valido

L’articolo fornisce un collegamento alla patch per un problema noto di Adobe Commerce 2.3.5, in cui ai clienti viene richiesto di effettuare l’accesso, ma il collegamento per inviare nuovamente un’e-mail di conferma non funziona.

## Prodotti e versioni interessati

* Adobe Commerce (tutti i metodi di implementazione) 2.3.5

## Problema

Adobe Commerce richiede ai clienti di effettuare l&#39;accesso visualizzando questo messaggio: *&quot;L&#39;account non è confermato. Fare clic qui per inviare di nuovo l&#39;e-mail di conferma&quot;*. Il collegamento **Fai clic qui** dovrebbe aprire la pagina di collegamento Invia conferma, ma non è attivo.

## Soluzione

Una patch per questo problema è disponibile nelle Risorse tecniche di Adobe Commerce: [Inviare nuovamente la patch del problema del collegamento e-mail di conferma dell&#39;account per Adobe Commerce 2.3.5](https://magento.com/tech-resources/download?_ga=2.193540264.409362045.1590506265-807369446.1578680711#download2368). Una correzione permanente sarà disponibile in Adobe Commerce 2.3.6, il cui rilascio è pianificato per il quarto trimestre del 2020.

Per istruzioni su come applicare una patch del compositore, vedere [Applicazione di una patch del compositore fornita dall&#39;Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md).

## Lettura correlata

Articoli nella knowledge base di supporto e nella documentazione per sviluppatori per problemi noti di Adobe Commerce 2.3.5:

* [Problema noto di Adobe Commerce 2.3.5: ordini di prodotti virtuali con più spedizioni](/help/troubleshooting/miscellaneous/magento-2-3-5-known-issue-virtual-product-multi-ship-orders.md)
* [Problema noto relativo al confronto dei prodotti in Adobe Commerce 2.3.5](/help/troubleshooting/storefront/product-comparison-known-issue-in-magento-2-3-5.md)
* [Adobe Commerce 2.3.5, 2.3.5-p1 patch: problema di pagamento paese](/help/troubleshooting/known-issues-patches-attached/magento-2-3-5-2-3-5-p1-patch-country-payment-issue.md)
* [Adobe Commerce richiede ai clienti di effettuare l’accesso a un collegamento non valido](/help/troubleshooting/known-issues-patches-attached/magento-prompts-customers-log-in-invalid-link.md)
* [Problema noto relativo al conteggio dei prodotti per azioni in blocco in Adobe Commerce 2.3.5](/help/troubleshooting/miscellaneous/bulk-action-product-count-known-issue-in-magento-2-3-5.md)
* [Patch per il problema di pagamento Amazon in Adobe Commerce 2.3.5-p1](/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md)
* [Problemi noti di Adobe Commerce 2.3.5](https://devdocs.magento.com/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues)
