---
title: "Adobe Commerce 2.4.0: Braintree non nel checkout di più indirizzi"
description: Questo articolo fornisce una soluzione alternativa per un problema noto di Adobe Commerce 2.4.0 in cui i metodi di pagamento Braintree non sono inclusi nell’utilizzo dell’estrazione di più indirizzi. Il problema è stato risolto in Adobe Commerce 2.4.1.
exl-id: efde0bba-fd4a-490b-becb-856cb9ea58a5
feature: Checkout, Compliance, Orders, Payments, Shipping/Delivery
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: Braintree non nel checkout di più indirizzi

Questo articolo fornisce una soluzione alternativa per un problema noto di Adobe Commerce 2.4.0 in cui i metodi di pagamento Braintree non sono inclusi nell’utilizzo dell’estrazione di più indirizzi. Il problema è stato risolto in Adobe Commerce 2.4.1.

Nota: Adobe Commerce consiglia di utilizzare [Commerce Marketplace estensione Braintree](https://marketplace.magento.com/paypal-module-braintree.html) per le versioni 2.3 e successive al fine di mantenere la conformità alle normative PSD. L’estensione non offre la funzionalità di estrazione con più indirizzi.

## Prodotti e versioni interessati

* Adobe Commerce on-premise v2.4.0
* Adobe Commerce su infrastruttura cloud v2.4.0

## Problema

<u>Prerequisiti</u>:

Viene utilizzata l’integrazione Braintree di base.

<u>Passaggi da riprodurre</u>:

1. Vai alla vetrina.
1. Accedi come cliente.
1. Aggiungi un prodotto al carrello.
1. Apri il carrello.
1. Premi **Visualizza e modifica carrello**.
1. Premi **Check-Out con più indirizzi**.
1. Premi **Vai a Informazioni spedizione**.
1. Premi **Continua con le informazioni di fatturazione**.

<u>Risultato previsto</u>:

La Braintree è disponibile come metodo di pagamento.

<u>Risultato effettivo</u>:

Braintree non disponibile come metodo di pagamento.

## Soluzione alternativa

Non abilitare le opzioni con più indirizzi se utilizzi Braintree in Adobe Commerce 2.4.0. Questo problema è stato risolto in Adobe Commerce 2.4.1.

## Lettura correlata nella knowledge base del supporto

* [Problema noto di Adobe Commerce 2.4.0: l’aggiornamento delle attività del cliente non funziona](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problema noto nella creazione di etichette di spedizione in Adobe Commerce 2.4.0](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
* [Problema noto di Adobe Commerce 2.4.0: visualizzazione dei dati dei messaggi non elaborati nella vetrina](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Problema noto di Adobe Commerce 2.4.0 - L’aliquota dell’imposta sull’esportazione non funziona](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problema noto di Adobe Commerce 2.4.0: il pulsante &quot;Aggiungi selezioni al carrello&quot; non funziona](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
