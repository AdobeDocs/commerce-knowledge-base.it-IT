---
title: Problema noto di Adobe Commerce 2.4.0 - L’aliquota dell’imposta sull’esportazione non funziona
description: Questo articolo fornisce una soluzione per un problema noto di Adobe Commerce 2.4.0 in cui il pulsante **Esporta aliquote fiscali** non funziona.
exl-id: 29a34a1f-d23a-43cb-ac1f-8711ce25fa6c
feature: Data Import/Export, Orders
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---

# Problema noto di Adobe Commerce 2.4.0 - L’aliquota dell’imposta sull’esportazione non funziona

Questo articolo fornisce una soluzione per un problema noto di Adobe Commerce 2.4.0 in cui **Esporta aliquote fiscali** non funziona.

## Prodotti e versioni interessati

* Adobe Commerce sull’infrastruttura cloud 2.4.0
* Adobe Commerce on-premise 2.4.0

## Problema

<u>Passaggi da riprodurre:</u>

1. Vai al pannello di amministrazione di Commerce > **Negozi** > **Regole fiscali**.
1. Fai clic su **Aggiungi nuova regola fiscale** pulsante.
1. Fai clic sul testo della **Esporta aliquote fiscali** pulsante.

   ![magento_export_tax_rates.png](assets/mceclip0.png)

<u>Risultato previsto</u>:

A `tax_rates.csv` download di file contenenti aliquote fiscali.

<u>Risultato effettivo</u>:

Nessun file .csv scaricato.

## Soluzione

Soluzione alternativa:

Fai clic sul bordo inferiore sinistro del **Esporta aliquote fiscali** per esportare `tax_rates.csv` file.

![magento_export_tax_rates.png](assets/mceclip1.png)

Il problema verrà risolto in una patch 2.4.1.

## Lettura correlata

Nella nostra knowledge base di supporto:

* [Problema noto di Adobe Commerce 2.4.0: i metodi di pagamento Braintree non vengono visualizzati nel checkout di più indirizzi](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md).
* [Problema noto nella creazione di etichette di spedizione in Adobe Commerce 2.4.0](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md).
* [Problema noto di Adobe Commerce 2.4.0: l’aggiornamento delle attività del cliente non funziona](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md).
* [Problema noto di Adobe Commerce 2.4.0: visualizzazione dei dati dei messaggi non elaborati nella vetrina](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md).
* [Problema noto di Adobe Commerce 2.4.0: il pulsante &quot;Aggiungi selezioni al carrello&quot; non funziona](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md).
