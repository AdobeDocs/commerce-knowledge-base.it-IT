---
title: "Adobe Commerce 2.4.0: Errore di estrazione durante la selezione dei pagamenti locali"
description: "In questo articolo viene illustrata la soluzione di un problema noto in Adobe Commerce durante il pagamento, che si verifica quando viene visualizzato un messaggio di errore durante la selezione di un metodo di pagamento locale per alcuni paesi. Questo accade per i paesi: Belgio, Italia, Paesi Bassi, Polonia e Spagna."
exl-id: de2eafb0-d03c-4ff8-9615-0f2676d95848
feature: B2B, Categories, Checkout, Orders, Payments
role: Developer
source-git-commit: a8cc7ad0cb9cb111f5b9636ff18aef3b6ed44329
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: Errore di estrazione durante la selezione dei pagamenti locali

Questo articolo descrive una soluzione per un problema noto in Adobe Commerce durante il pagamento, che si verifica quando viene visualizzato un messaggio di errore durante la selezione di un metodo di pagamento locale per alcuni paesi. Ciò si verifica per i paesi: Belgio, Italia, Paesi Bassi, Polonia e Spagna.

Il messaggio di errore &quot;*Non sono attualmente disponibili metodi di pagamento. Aggiorna l&#39;indirizzo di fatturazione.*&quot; verrà visualizzato, ma i metodi di pagamento locali continueranno a essere visualizzati e a funzionare correttamente. Una correzione permanente sarà disponibile in Adobe Commerce 2.4.1.

## Prodotti e versioni interessati

* Adobe Commerce on-premise 2.4.0
* Adobe Commerce sull’infrastruttura cloud 2.4.0

## Problema

<u>Prerequisiti</u>:

* Adobe Commerce 2.4.0 è installato.
* Crea un prodotto e una categoria.
* Configura [Braintree metodo di pagamento](https://developer.adobe.com/commerce/webapi/graphql/payment-methods/braintree.html).

<u>Passaggi da riprodurre</u>:

1. Passa alla vetrina.
1. Seleziona gli elementi da aggiungere al carrello.
1. Procedi con il pagamento.
1. Compila il modulo dell’indirizzo con un indirizzo valido.
1. Passare alla pagina Revisione e pagamenti.

<u>Risultato previsto</u>:

I metodi di pagamento locali dovrebbero essere visualizzati normalmente, senza un messaggio di errore.

<u>Risultato effettivo</u>:

Il messaggio di errore &quot;*Non sono attualmente disponibili metodi di pagamento. Aggiorna l&#39;indirizzo di fatturazione.Viene visualizzato*&quot;, ma i metodi di pagamento locali continueranno a essere visualizzati e funzioneranno correttamente.

## Soluzione

La soluzione consiste nell&#39;ignorare il messaggio di errore visualizzato e continuare con il pagamento come di consueto, in quanto tutti i metodi di pagamento locali funzioneranno normalmente. La correzione era disponibile a partire da Adobe Commerce versione 2.4.1.

## Lettura correlata

* [Problema noto di Adobe Commerce 2.4.0: visualizzazione dei dati dei messaggi non elaborati nella vetrina](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Problema noto di Adobe Commerce 2.4.0: l’esportazione delle aliquote fiscali non funziona](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problema noto di Adobe Commerce 2.4.0: i metodi di pagamento Braintree non vengono visualizzati nel checkout di più indirizzi](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problema noto di Adobe Commerce 2.4.0: l’aggiornamento delle attività del cliente non funziona](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [L’amministratore B2B di Adobe Commerce 2.4.0 non può aggiungere un prodotto configurabile all’offerta](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
