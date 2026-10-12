---
title: 'Adobe Commerce 2.4.2 B2B: lo sconto rimane la modifica del metodo di pagamento'
description: Questo articolo descrive un problema noto di Adobe Commerce 2.4.2 B2B in cui uno sconto legato al metodo di pagamento persiste dopo una modifica del metodo di pagamento al momento del pagamento. Al momento non è disponibile alcuna risoluzione.
exl-id: cd863852-403b-404f-8717-c78c238f5f33
feature: B2B, Orders, Payments, Personalization
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: f37757d8-3174-5335-b977-1161792f965d
    internal-label: Personalization
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
source-wordcount: '210'
ht-degree: 0%
---
# Adobe Commerce 2.4.2 B2B: lo sconto rimane la modifica del metodo di pagamento

Questo articolo descrive un problema noto di Adobe Commerce 2.4.2 B2B in cui uno sconto legato al metodo di pagamento persiste dopo una modifica del metodo di pagamento al momento del pagamento. Al momento non è disponibile alcuna risoluzione.

## Prodotti e versioni interessati

* Adobe Commerce 2.4.2
* Adobe Commerce sull’infrastruttura cloud 2.4.2
* B2B per Adobe Commerce 1.3.1


## Problema

<u>Passaggi da riprodurre</u>:

1. Crea un carrello **Regola prezzo** legato a un metodo di pagamento (esempio: gli utenti Paypal ricevono uno sconto del 20%).
1. Creare un ordine di acquisto e selezionare Paypal come metodo di pagamento. Viene applicato lo sconto.
1. L&#39;ordine di acquisto viene approvato.
1. Vai alla pagina di pagamento per completare l&#39;ordine.
1. Seleziona un altro metodo di pagamento.

<u>Risultati effettivi</u>:

Lo sconto per il metodo di pagamento rimane applicato al totale dell&#39;ordine.  Nessun messaggio di errore visualizzato.Il proprietario dell&#39;archivio potrà vedere se ciò si è verificato verificando la cronologia degli ordini.

<u>Risultati previsti</u> Lo sconto per il metodo di pagamento :The è stato rimosso dal totale dell&#39;ordine, come previsto.

## Soluzione

Al momento non è disponibile alcuna risoluzione.
