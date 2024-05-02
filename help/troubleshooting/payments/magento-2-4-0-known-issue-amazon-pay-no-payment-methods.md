---
title: "Problema noto di Adobe Commerce 2.4.0: Amazon pay, nessun metodo di pagamento"
description: Questo articolo fornisce una soluzione per un problema noto di Adobe Commerce 2.4.0 in cui mancano i metodi di pagamento quando i clienti utilizzano **Return to standard checkout**, dopo aver abilitato Amazon pay.
exl-id: efd792c7-8970-4366-b9d1-4bf284ea96db
feature: B2B, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 problema noto: Amazon pay, nessun metodo di pagamento

Questo articolo fornisce una soluzione per un problema noto di Adobe Commerce 2.4.0 in cui i metodi di pagamento mancano quando i clienti utilizzano **Torna al pagamento standard**, dopo aver abilitato Amazon pay.

## Prodotti e versioni interessati

Adobe Commerce on-premise e Adobe Commerce on cloud infrastructure v2.3.5.p1 e v2.4.0

<u>Passaggi da riprodurre:</u>

1. Passa alla vetrina.
1. Aggiungi qualsiasi elemento al carrello e procedi al pagamento.
1. Accedi al tuo account Amazon Pay.
1. Seleziona un indirizzo e procedi al pagamento.
1. Clic **Torna al pagamento standard**.
1. Procedi al pagamento.

<u>Risultati previsti:</u>

I metodi di pagamento devono essere visualizzati dopo il riavvio del pagamento.

<u>Risultati effettivi:</u>

Metodi di pagamento mancanti.

## Soluzione

È prevista una risoluzione per la versione 2.4.1.

## Letture correlate nella knowledge base di supporto:

* [Problema noto di Adobe Commerce 2.4.0: messaggio di errore durante la selezione del metodo di pagamento locale visualizzato per alcuni paesi durante l’acquisto](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Problema noto di Adobe Commerce 2.4.0: errore 404 durante la rimozione dei punti premio in caso di pagamento tramite multi-shipping](/help/troubleshooting/storefront/magento-2-4-0-404-error-removing-rewards-points-on-multi-shipping-checkout.md)
* [Problema noto di Adobe Commerce 2.4.0: errore di visualizzazione degli ordini](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [L’amministratore B2B di Adobe Commerce 2.4.0 non può aggiungere un prodotto configurabile all’offerta](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Problema noto di Adobe Commerce 2.4.0: i metodi di pagamento Braintree non vengono visualizzati nel checkout di più indirizzi](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problema noto nella creazione di etichette di spedizione in Adobe Commerce 2.4.0](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
* [Problema noto di Adobe Commerce 2.4.0: l’aggiornamento delle attività del cliente non funziona](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problema noto di Adobe Commerce 2.4.0 - L’aliquota dell’imposta sull’esportazione non funziona](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problema noto di Adobe Commerce 2.4.0: il pulsante &quot;Aggiungi selezioni al carrello&quot; non funziona](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
* [Problema noto di Adobe Commerce 2.4.0: visualizzazione dei dati dei messaggi non elaborati nella vetrina](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
