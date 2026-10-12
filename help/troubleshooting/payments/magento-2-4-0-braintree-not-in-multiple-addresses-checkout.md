---
title: 'Adobe Commerce 2.4.0: estrazione di Braintree non in più indirizzi'
description: Questo articolo fornisce una soluzione alternativa per un problema noto di Adobe Commerce 2.4.0 in cui i metodi di pagamento di Braintree non sono inclusi nell’utilizzo del pagamento tramite più indirizzi. Il problema è stato risolto in Adobe Commerce 2.4.1.
exl-id: efde0bba-fd4a-490b-becb-856cb9ea58a5
feature: Checkout, Compliance, Orders, Payments, Shipping/Delivery
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
    internal-label: Compliance
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: 04d3134c-2afb-5bd7-ac14-e19fa935e848
    internal-label: Shipping/Delivery
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%
---
# Adobe Commerce 2.4.0: estrazione di Braintree non in più indirizzi

Questo articolo fornisce una soluzione alternativa per un problema noto di Adobe Commerce 2.4.0 in cui i metodi di pagamento di Braintree non sono inclusi nell’utilizzo del pagamento tramite più indirizzi. Il problema è stato risolto in Adobe Commerce 2.4.1.

Nota: Adobe Commerce consiglia di utilizzare l&#39;estensione [Commerce Marketplace Braintree](https://marketplace.magento.com/paypal-module-braintree.html) per le versioni 2.3 e successive per mantenere la conformità a PSD. L’estensione non offre la funzionalità di estrazione con più indirizzi.

## Prodotti e versioni interessati

* Adobe Commerce on-premise v2.4.0
* Adobe Commerce su infrastruttura cloud v2.4.0

## Problema

<u>Prerequisiti</u>:

Viene utilizzata l’integrazione di base con Braintree.

<u>Passaggi da riprodurre</u>:

1. Vai alla vetrina.
1. Accedi come cliente.
1. Aggiungi un prodotto al carrello.
1. Apri il carrello.
1. Premere **Visualizza e modifica carrello**.
1. Premere **Estrai con più indirizzi**.
1. Premi **Vai alle informazioni sulla spedizione**.
1. Premi **Continua con le informazioni di fatturazione**.

<u>Risultato previsto</u>:

Braintree è disponibile come metodo di pagamento.

<u>Risultato effettivo</u>:

Braintree non è disponibile come metodo di pagamento.

## Soluzione alternativa

Non abilitare le opzioni con più indirizzi se si utilizza Braintree in Adobe Commerce 2.4.0. Questo problema è stato risolto in Adobe Commerce 2.4.1.
