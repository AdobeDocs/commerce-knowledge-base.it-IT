---
title: '"Adobe Commerce 2.4.0: "Aggiungere selezioni al carrello" non funziona"'
description: Questo articolo fornisce una soluzione alternativa per un problema noto relativo a un pulsante danneggiato nell’amministratore di Commerce durante la gestione del carrello acquisti di un cliente. Quando si tenta di aggiungere prodotti selezionati al carrello di un cliente, il pulsante **Aggiungi selezioni al carrello** situato nella parte inferiore della sezione non funziona. Questo problema si verifica in qualsiasi pagina del pannello di amministrazione che contiene due pulsanti **Aggiungi selezioni al carrello**. Una correzione permanente sarà disponibile in Adobe Commerce 2.4.1.
exl-id: b0830ec2-2aea-4afb-8d02-e9c8f54283be
feature: Orders, Shopping Cart
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: &quot;Aggiungi selezioni al carrello&quot; non funziona

Questo articolo fornisce una soluzione alternativa per un problema noto relativo a un pulsante danneggiato nell’amministratore di Commerce durante la gestione del carrello acquisti di un cliente. Quando tenti di aggiungere prodotti selezionati al carrello di un cliente, il **Aggiungi selezioni al carrello** nella parte inferiore della sezione. Questo problema si verifica su qualsiasi pagina del pannello di amministrazione che contiene due **Aggiungi selezioni al carrello** pulsanti. Una correzione permanente sarà disponibile in Adobe Commerce 2.4.1.

## Prodotti e versioni interessati

* Adobe Commerce 2.4.0 (tutti i metodi di distribuzione)

## Problema

<u>Passaggi da riprodurre</u>

1. Passa a qualsiasi pagina del pannello di amministrazione che contiene due **Aggiungi selezioni al carrello** pulsanti.
1. Seleziona gli oggetti da aggiungere al carrello.
1. Fai clic su **Aggiungi selezioni al carrello** nella parte inferiore della sezione.

<u>Risultato previsto</u>

Tutte le selezioni vengono aggiunte al carrello come previsto.

<u>Risultato effettivo</u>

Adobe Commerce non aggiunge le tue selezioni al carrello.

## Soluzione

Il **Aggiungi selezioni al carrello** il pulsante situato nella parte superiore della pagina è ancora funzionante. Il problema dovrebbe essere risolto in Adobe Commerce versione 2.4.1, il cui rilascio è pianificato per il quarto trimestre del 2010.

## Lettura correlata

* [Gestione di un carrello da parte dei documenti di marketing](https://docs.magento.com/user-guide/sales/shopping-assisted-cart-manage.html) nella guida utente.
* [Problema noto di Adobe Commerce 2.4.0: visualizzazione dei dati dei messaggi non elaborati nella vetrina](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md) nella nostra knowledge base di supporto.
* [Problema noto di Adobe Commerce 2.4.0: l’esportazione delle aliquote fiscali non funziona](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md) nella nostra knowledge base di supporto.
* [Problema noto di Adobe Commerce 2.4.0: i metodi di pagamento Braintree non vengono visualizzati nel checkout di più indirizzi](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md) nella nostra knowledge base di supporto.
