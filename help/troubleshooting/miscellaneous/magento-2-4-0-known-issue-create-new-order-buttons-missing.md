---
title: "Problema noto di Adobe Commerce 2.4.0: pulsanti Crea nuovo ordine mancanti"
description: Questo articolo fornisce una soluzione alternativa a un problema noto in Commerce Admin per due pulsanti mancanti nella pagina di creazione dell’ordine. Durante la creazione di un nuovo ordine per un cliente nuovo o esistente, non è possibile aggiungere prodotti all’ordine dal catalogo perché mancano i pulsanti **Aggiungi prodotti per SKU** e **Aggiungi prodotti**. La causa è l’attivazione del bundling JS. Una correzione sarà disponibile in Adobe Commerce 2.4.1.
exl-id: 24ae880e-6d74-4444-9165-2744b12af81a
feature: B2B
role: Developer
source-git-commit: a1046621259ea49eab74cd6ba3bba550e0c70283
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# Problema noto di Adobe Commerce 2.4.0: pulsanti Crea nuovo ordine mancanti

Questo articolo fornisce una soluzione alternativa a un problema noto in Commerce Admin per due pulsanti mancanti nella pagina di creazione dell’ordine. Durante la creazione di un nuovo ordine per un cliente nuovo o esistente, non è possibile aggiungere prodotti all&#39;ordine dal catalogo perché mancano i pulsanti **Aggiungi prodotti per SKU** e **Aggiungi prodotti**. La causa è l’attivazione del bundling JS. Una correzione sarà disponibile in Adobe Commerce 2.4.1.

## Prodotti e versioni interessati

* Adobe Commerce on-premise 2.4.0
* Adobe Commerce sull’infrastruttura cloud 2.4.0

## Problema

<u>Passaggi da riprodurre</u>

1. Vai a **Clienti > Tutti i clienti**.
1. Fai clic sul collegamento **Modifica** su un cliente.
1. Fai clic sul pulsante **Crea ordine**.

<u>Risultato previsto</u>

I pulsanti **Aggiungi prodotti per SKU** e **Aggiungi prodotti** sono disponibili nella pagina **Crea nuovo ordine**.

<u>Risultato effettivo</u>

I pulsanti **Aggiungi prodotti per SKU** e **Aggiungi prodotti** non sono presenti nella pagina **Crea nuovo ordine**.

## Soluzione alternativa

La soluzione alternativa per questo problema consiste nel disabilitare il bundling JS per l’istanza Adobe Commerce. Il problema dovrebbe essere risolto in Adobe Commerce 2.4.1, il cui rilascio è pianificato per il quarto trimestre del 2020.

## Letture correlate nella knowledge base di supporto

* [Problema noto di Adobe Commerce 2.4.0: visualizzazione dei dati dei messaggi non elaborati nella vetrina](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Problema noto di Adobe Commerce 2.4.0: l’esportazione delle aliquote fiscali non funziona](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problema noto di Adobe Commerce 2.4.0: i metodi di pagamento Braintree non vengono visualizzati nel checkout di più indirizzi](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problema noto di Adobe Commerce 2.4.0: messaggio di errore durante la selezione del metodo di pagamento locale visualizzato per alcuni paesi durante l’acquisto](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Problema noto di Adobe Commerce 2.4.0: errore 404 durante la rimozione dei punti premio in caso di pagamento tramite multi-shipping](/help/troubleshooting/storefront/magento-2-4-0-404-error-removing-rewards-points-on-multi-shipping-checkout.md)
* [Problema noto di Adobe Commerce 2.4.0: errore di visualizzazione degli ordini](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [L’amministratore B2B di Adobe Commerce 2.4.0 non può aggiungere un prodotto configurabile all’offerta](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Problema noto di Adobe Commerce 2.4.0: l’aggiornamento delle attività del cliente non funziona](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problema noto di Adobe Commerce 2.4.0: il pulsante &quot;Aggiungi selezioni al carrello&quot; non funziona](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
