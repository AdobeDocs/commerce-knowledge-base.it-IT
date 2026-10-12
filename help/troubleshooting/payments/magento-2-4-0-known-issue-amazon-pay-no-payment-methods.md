---
title: 'Adobe Commerce 2.4.0 problema noto: Amazon pay, nessun metodo di pagamento'
description: Questo articolo fornisce una soluzione per un problema noto di Adobe Commerce 2.4.0 in cui mancano i metodi di pagamento quando i clienti utilizzano **Return to standard checkout**, dopo aver abilitato Amazon pay.
exl-id: efd792c7-8970-4366-b9d1-4bf284ea96db
feature: B2B, Orders, Payments
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%
---
# Adobe Commerce 2.4.0 problema noto: Amazon pay, nessun metodo di pagamento

Questo articolo fornisce una soluzione per un problema noto di Adobe Commerce 2.4.0 in cui mancano i metodi di pagamento quando i clienti utilizzano **Torna all&#39;estrazione standard**, dopo aver abilitato Amazon Pay.

## Prodotti e versioni interessati

Adobe Commerce on-premise e Adobe Commerce on cloud infrastructure v2.3.5.p1 e v2.4.0

<u>Passaggi da riprodurre:</u>

1. Passa alla vetrina.
1. Aggiungi qualsiasi elemento al carrello e procedi al pagamento.
1. Accedi al tuo account Amazon Pay.
1. Seleziona un indirizzo e procedi al pagamento.
1. Fai clic su **Torna all&#39;estrazione standard**.
1. Procedi al pagamento.

<u>Risultati previsti:</u>

I metodi di pagamento devono essere visualizzati dopo il riavvio del pagamento.

<u>Risultati effettivi:</u>

Metodi di pagamento mancanti.

## Soluzione

È prevista una risoluzione per la versione 2.4.1.

## Letture correlate nella knowledge base di supporto:

* [Problema noto di Adobe Commerce 2.4.0: messaggio di errore durante la selezione del metodo di pagamento locale visualizzato per alcuni paesi durante l’acquisto](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Problema noto di Adobe Commerce 2.4.0: i metodi di pagamento di Braintree non vengono visualizzati nell’estrazione di più indirizzi](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
