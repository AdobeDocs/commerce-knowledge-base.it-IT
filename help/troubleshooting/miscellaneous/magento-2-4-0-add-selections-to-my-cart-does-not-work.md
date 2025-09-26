---
title: 'Adobe Commerce 2.4.0: "Aggiungi selezioni al carrello" non funziona'
description: Questo articolo fornisce una soluzione alternativa per un problema noto relativo a un pulsante danneggiato nell’amministratore di Commerce durante la gestione del carrello acquisti di un cliente. Quando si tenta di aggiungere prodotti selezionati al carrello di un cliente, il pulsante **Aggiungi selezioni al carrello** situato nella parte inferiore della sezione non funziona. Questo problema si verifica in qualsiasi pagina del pannello di amministrazione che contiene due pulsanti **Aggiungi selezioni al carrello**. Una correzione permanente sarà disponibile in Adobe Commerce 2.4.1.
exl-id: b0830ec2-2aea-4afb-8d02-e9c8f54283be
feature: Orders, Shopping Cart
role: Developer
source-git-commit: 9cd9720a73b8ecde3baf6a7a5b5732ad1330feee
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: &quot;Aggiungi selezioni al carrello&quot; non funziona

Questo articolo fornisce una soluzione alternativa per un problema noto relativo a un pulsante danneggiato nell’amministratore di Commerce durante la gestione del carrello acquisti di un cliente. Quando si tenta di aggiungere prodotti selezionati al carrello di un cliente, il pulsante **Aggiungi selezioni al carrello** nella parte inferiore della sezione non funziona. Questo problema si verifica in qualsiasi pagina del pannello di amministrazione contenente due **pulsanti Aggiungi selezioni al carrello**. Una correzione permanente sarà disponibile in Adobe Commerce 2.4.1.

## Prodotti e versioni interessati

* Adobe Commerce 2.4.0 (tutti i metodi di distribuzione)

## Problema

<u>Passaggi da riprodurre</u>

1. Passa a qualsiasi pagina del pannello di amministrazione contenente due **Aggiungi selezioni al carrello**.
1. Seleziona gli oggetti da aggiungere al carrello.
1. Fai clic sul pulsante **Aggiungi selezioni al carrello** nella parte inferiore della sezione.

<u>Risultato previsto</u>

Tutte le selezioni vengono aggiunte al carrello come previsto.

<u>Risultato effettivo</u>

Adobe Commerce non aggiunge le tue selezioni al carrello.

## Soluzione

Il pulsante **Aggiungi selezioni al carrello** nella parte superiore della pagina è ancora funzionante. Il problema dovrebbe essere risolto in Adobe Commerce versione 2.4.1, il cui rilascio è pianificato per il quarto trimestre del 2010.

## Lettura correlata

* [MerchDocs&#39; Gestione di un carrello](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/point-of-purchase/assist/shopping-assisted-cart-manage) nella guida utente.
* [Problema noto di Adobe Commerce 2.4.0: l&#39;esportazione delle aliquote fiscali non funziona](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md) nella Knowledge Base di supporto.
* [Problema noto di Adobe Commerce 2.4.0: i metodi di pagamento di Braintree non vengono visualizzati nell&#39;estrazione di più indirizzi](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md) nella Knowledge Base del supporto tecnico.
