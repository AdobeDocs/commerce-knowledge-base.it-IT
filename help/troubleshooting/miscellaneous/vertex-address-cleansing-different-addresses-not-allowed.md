---
title: 'Pulizia degli indirizzi verticali: indirizzi diversi non consentiti'
description: Questo articolo descrive la soluzione del problema per cui, quando l’utente tenta di inserire un indirizzo di fatturazione e spedizione **diverso** con la convalida degli indirizzi verticali abilitata, la vetrina non consente all’utente di inserirlo.
exl-id: a481b044-3b74-4792-abc6-249a182c49e1
feature: B2B, Orders, Shipping/Delivery, Checkout
role: Developer
source-git-commit: 7cf1167bce8cef51b206b6cc1d75214288f9cb1c
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# Pulizia degli indirizzi verticali: indirizzi diversi non consentiti

In questo articolo viene illustrata la soluzione del problema per cui quando l&#39;utente tenta di immettere un indirizzo di fatturazione e spedizione **diverso**, con la convalida degli indirizzi verticali abilitata, la vetrina non consente all&#39;utente di immetterlo.

## Prodotti e versioni interessati

* Adobe Commerce on-premise e Adobe Commerce sull’infrastruttura cloud 2.3.5-p1

## Problema

<u>Passaggi da riprodurre</u>:

1. Vai a Amministratore > **Archivi** > **Configurazione** > **Vendite** > **Pulizia indirizzi**.
1. Seleziona *Abilitato* dal menu a discesa **Usa pulizia indirizzi verticali** e **Salva configurazione**.
1. Vai al front-end come ospite e aggiungi un prodotto al carrello.
1. Fai clic sull&#39;icona del carrello e **Procedi all&#39;estrazione**.
1. Compila i campi indirizzo.
1. Seleziona il **metodo di spedizione** desiderato e fai clic su **Avanti**.
1. Fai di nuovo clic sul pulsante **Avanti**.
1. Deseleziona **Il mio indirizzo di fatturazione e spedizione** **sono uguali** e immetti un nuovo indirizzo di fatturazione (diverso da Indirizzo).
1. Fare clic sul pulsante **Aggiorna**, quindi su **Aggiorna indirizzo**.

<u>Risultati previsti</u>:

L’utente visualizza diversi indirizzi di fatturazione e spedizione.

<u>Risultati effettivi</u>:

Quando l’utente preme il tasto Aggiorna, gli indirizzi di fatturazione e di spedizione diventano gli stessi.

## Causa

Verifica indirizzo vertice non riuscita.

## Soluzione

Disattiva la verifica degli indirizzi verticali o esegui l’aggiornamento alla versione 2.4.0.

## Lettura correlata

* [Problema noto di Adobe Commerce 2.4.0: messaggio di errore durante la selezione del metodo di pagamento locale visualizzato per alcuni paesi durante l’acquisto](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [L’amministratore B2B di Adobe Commerce 2.4.0 non può aggiungere un prodotto configurabile all’offerta](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Problema noto di Adobe Commerce 2.4.0: i metodi di pagamento di Braintree non vengono visualizzati nell’estrazione di più indirizzi](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problema noto di Adobe Commerce 2.4.0: l’aggiornamento delle attività del cliente non funziona](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problema noto di Adobe Commerce 2.4.0 - L’aliquota dell’imposta sull’esportazione non funziona](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problema noto di Adobe Commerce 2.4.0: il pulsante &quot;Aggiungi selezioni al carrello&quot; non funziona](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
* [Adobe Commerce 2.4.0 problema noto: etichetta &quot;Refund&quot; mancante in Klarna](/help/troubleshooting/payments/magento-2-4-0-known-issue-missing-refund-label-in-klarna.md)
* [Problema noto di Adobe Commerce 2.4.0: due pulsanti mancanti nella pagina Crea nuovo ordine in Amministratore](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-create-new-order-buttons-missing.md)
* [Problema noto di Adobe Commerce 2.4.0: quando Braintree è abilitato, l’emissione di fattura parziale Venmo](/help/troubleshooting/payments/magento-2-4-0-2-4-1-enable-braintree-venmo-partial-invoice-issue.md)
* [Problema noto di Adobe Commerce 2.4.0: messaggio di errore durante la selezione del metodo di pagamento locale visualizzato per alcuni paesi durante l’acquisto](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Problema noto di Adobe Commerce 2.4.0: Amazon Pay abilitato, metodi di pagamento mancanti quando viene utilizzato il metodo Return to standard checkout](/help/troubleshooting/payments/magento-2-4-0-known-issue-amazon-pay-no-payment-methods.md)
* [Problema noto di Adobe Commerce 2.4.0: l’installazione della versione 2.4.0 non riesce e la cache degli archivi è obsoleta](/help/troubleshooting/installation-and-upgrade/magento-2-4-0-known-issue-2-4-0-installation-fails-with-outdated-stores-cache.md)
