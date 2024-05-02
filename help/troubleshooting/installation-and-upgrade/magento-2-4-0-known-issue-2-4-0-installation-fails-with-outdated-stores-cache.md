---
title: L’installazione di Adobe Commerce 2.4.0 non riesce se la cache degli archivi è obsoleta
description: "Questo articolo fornisce una soluzione al problema in cui l’installazione di Adobe Commerce 2.4.0 non riesce e viene visualizzato il messaggio di errore: *Il sito web predefinito non è definito. Imposta il sito web e riprova.* visualizzato nella console."
exl-id: 0680199b-7e47-4a8c-91fe-9f6c32839a0e
feature: B2B, Cache, Console, Install, Upgrade
role: Developer
source-git-commit: 2bba3af8919e1db8482764b8d688f95e606c2683
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# L’installazione di Adobe Commerce 2.4.0 non riesce se la cache degli archivi è obsoleta

Questo articolo fornisce una soluzione al problema relativo al mancato funzionamento dell’installazione di Adobe Commerce 2.4.0 con il messaggio di errore: *Il sito Web predefinito non è definito. Imposta il sito web e riprova.* nella console.

## Prodotti e versioni interessati

* Adobe Commerce sull’infrastruttura cloud 2.4.0
* Adobe Commerce on-premise 2.4.0

## Problema

<u>Prerequisiti:</u>
Un’estensione di terze parti con dipendenze dalle API per il modulo Store nei comandi CLI è configurata come richiesto in `composer.json`. In questo modo, l’installazione di Adobe Commerce 2.4.0 non riesce e viene visualizzato un messaggio di errore: *Il sito Web predefinito non è definito. Imposta il sito web e riprova.* nella console.

## Causa

Il problema viene visualizzato per le estensioni di terze parti che hanno dipendenze dagli archivi nei loro comandi CLI. Uno è Amazon Sales Channel.

## Soluzione

Prima dell’installazione di Adobe Commerce 2.4.0, i commercianti devono:

1. Rimuovi queste estensioni di terze parti da `composer.json`.
1. Installa Adobe Commerce senza estensioni.
1. Aggiungi le estensioni dopo l’installazione.

Il problema verrà risolto nell’ambito della versione 2.4.1.

## Letture correlate nella knowledge base di supporto:

* [Adobe Commerce 2.4.0 problema noto: etichetta &quot;Refund&quot; mancante in Klarna](/help/troubleshooting/payments/magento-2-4-0-known-issue-missing-refund-label-in-klarna.md)
* [Problema noto di Adobe Commerce 2.4.0: due pulsanti mancanti nella pagina Crea nuovo ordine in Amministratore](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-create-new-order-buttons-missing.md)
* [Adobe Commerce 2.4.0, 2.4.1: Abilitare l’emissione di fattura parziale Braintree Venmo](/help/troubleshooting/payments/magento-2-4-0-2-4-1-enable-braintree-venmo-partial-invoice-issue.md)
* [Problema noto di Adobe Commerce 2.4.0: messaggio di errore durante la selezione del metodo di pagamento locale visualizzato per alcuni paesi durante l’acquisto](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Problema noto di Adobe Commerce 2.4.0: Amazon Pay abilitato, metodi di pagamento mancanti quando viene utilizzato il metodo Return to standard checkout](/help/troubleshooting/payments/magento-2-4-0-known-issue-amazon-pay-no-payment-methods.md)
* [Problema noto di Adobe Commerce 2.4.0: errore 404 durante la rimozione dei punti premio in caso di pagamento tramite multi-shipping](/help/troubleshooting/storefront/magento-2-4-0-404-error-removing-rewards-points-on-multi-shipping-checkout.md)
* [Problema noto di Adobe Commerce 2.4.0: errore di visualizzazione degli ordini](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [L’amministratore B2B di Adobe Commerce 2.4.0 non può aggiungere un prodotto configurabile all’offerta](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Problema noto di Adobe Commerce 2.4.0: i metodi di pagamento Braintree non vengono visualizzati nel checkout di più indirizzi](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problema noto nella creazione di etichette di spedizione in Adobe Commerce 2.4.0](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
* [Problema noto di Adobe Commerce 2.4.0: l’aggiornamento delle attività del cliente non funziona](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problema noto di Adobe Commerce 2.4.0 - L’aliquota dell’imposta sull’esportazione non funziona](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problema noto di Adobe Commerce 2.4.0: il pulsante &quot;Aggiungi selezioni al carrello&quot; non funziona](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
* [Problema noto di Adobe Commerce 2.4.0: visualizzazione dei dati dei messaggi non elaborati nella vetrina](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
