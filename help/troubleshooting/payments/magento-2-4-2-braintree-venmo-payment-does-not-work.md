---
title: 'Adobe Commerce 2.4.2: il pagamento Braintree Venmo non funziona'
description: Questo articolo descrive un problema noto di Adobe Commerce 2.4.2 in cui non vengono generati ordini quando si utilizza Braintree Venmo durante il pagamento. Al momento non è disponibile alcuna risoluzione.
exl-id: 1832ab64-5024-444b-915e-473b34979a6e
feature: Orders, Payments
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%
---
# Adobe Commerce 2.4.2: il pagamento Braintree Venmo non funziona

Questo articolo descrive un problema noto di Adobe Commerce 2.4.2 in cui non vengono generati ordini quando si utilizza Braintree Venmo durante il pagamento. Al momento non è disponibile alcuna risoluzione.

## Prodotti e versioni interessati

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2

## Problema

<u>Precondizione</u>:

Abilita il pagamento Venmo nella configurazione Braintree.

<u>Passaggi da riprodurre</u>:

1. Nella vetrina, aggiungi qualsiasi elemento al carrello.
1. Procedi a **Estrai**.
1. Selezionare il metodo di spedizione appropriato.
1. Seleziona **Venmo** come metodo di pagamento.
1. Fai clic su **Paga con Venmo**.
1. Fai clic su **Ordina**.

<u>Risultati effettivi</u>:

L’ordine non viene creato nel codice Adobe Commerce dopo che il cliente viene reindirizzato allo store dall’app Venmo e non viene visualizzato alcun messaggio di errore. L’ordine viene creato in Braintree.

<u>Risultati previsti</u>:

L’ordine viene creato in Adobe Commerce dopo che il cliente viene reindirizzato allo store dall’app Venmo e viene creato in Braintree, come previsto.

## Soluzione

Al momento non è disponibile alcuna risoluzione.
