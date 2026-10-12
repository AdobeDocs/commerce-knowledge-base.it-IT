---
title: L’installazione di Adobe Commerce 2.4.0 non riesce se la cache degli archivi è obsoleta
description: 'Questo articolo fornisce una soluzione al problema in cui l’installazione di Adobe Commerce 2.4.0 non riesce e viene visualizzato il messaggio di errore: *Il sito web predefinito non è definito. Imposta il sito web e riprova.* visualizzato nella console.'
exl-id: 0680199b-7e47-4a8c-91fe-9f6c32839a0e
feature: B2B, Cache, Console, Install, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: c4af0798-d497-5e6b-8380-19812c26d00a
    internal-label: Console
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%
---
# L’installazione di Adobe Commerce 2.4.0 non riesce se la cache degli archivi è obsoleta

In questo articolo viene fornita una soluzione al problema che causa l&#39;errore dell&#39;installazione di Adobe Commerce 2.4.0 con il messaggio di errore: *Il sito Web predefinito non è definito. Impostare il sito Web e riprovare.* nella console.

## Prodotti e versioni interessati

* Adobe Commerce sull’infrastruttura cloud 2.4.0
* Adobe Commerce on-premise 2.4.0

## Problema

<u>Prerequisiti:</u>
Un&#39;estensione di terze parti con dipendenze dalle API per il modulo Store nei comandi CLI è configurata come richiesto in `composer.json`. In questo modo l&#39;installazione di Adobe Commerce 2.4.0 non riesce e viene visualizzato un messaggio di errore: *Il sito Web predefinito non è definito. Impostare il sito Web e riprovare.* nella console.

## Causa

Il problema viene visualizzato per le estensioni di terze parti che hanno dipendenze dagli archivi nei loro comandi CLI. Uno è Amazon Sales Channels.

## Soluzione

Prima dell’installazione di Adobe Commerce 2.4.0, i commercianti devono:

1. Rimuovi queste estensioni di terze parti da `composer.json`.
1. Installa Adobe Commerce senza estensioni.
1. Aggiungi le estensioni dopo l’installazione.

Il problema verrà risolto nell’ambito della versione 2.4.1.

## Letture correlate nella knowledge base di supporto:

* [Adobe Commerce 2.4.0 problema noto: etichetta &quot;Refund&quot; mancante in Klarna](/help/troubleshooting/payments/magento-2-4-0-known-issue-missing-refund-label-in-klarna.md)
* [Adobe Commerce 2.4.0, 2.4.1: Abilitare l’emissione di fattura parziale di Braintree Venmo](/help/troubleshooting/payments/magento-2-4-0-2-4-1-enable-braintree-venmo-partial-invoice-issue.md)
* [Problema noto di Adobe Commerce 2.4.0: messaggio di errore durante la selezione del metodo di pagamento locale visualizzato per alcuni paesi durante l’acquisto](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Problema noto di Adobe Commerce 2.4.0: Amazon Pay abilitato, metodi di pagamento mancanti quando viene utilizzato il metodo Return to standard checkout](/help/troubleshooting/payments/magento-2-4-0-known-issue-amazon-pay-no-payment-methods.md)
* [Problema noto di Adobe Commerce 2.4.0: i metodi di pagamento di Braintree non vengono visualizzati nell’estrazione di più indirizzi](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)

