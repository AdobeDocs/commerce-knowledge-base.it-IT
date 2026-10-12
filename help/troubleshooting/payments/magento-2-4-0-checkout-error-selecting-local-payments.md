---
title: 'Adobe Commerce 2.4.0: Errore di estrazione durante la selezione dei pagamenti locali'
description: 'Questo articolo descrive una soluzione per un problema noto in Adobe Commerce durante il pagamento, che si verifica quando viene visualizzato un messaggio di errore durante la selezione di un metodo di pagamento locale per alcuni paesi. Ciò si verifica per i paesi: Belgio, Italia, Paesi Bassi, Polonia e Spagna.'
exl-id: de2eafb0-d03c-4ff8-9615-0f2676d95848
feature: B2B, Categories, Checkout, Orders, Payments
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%
---
# Adobe Commerce 2.4.0: Errore di estrazione durante la selezione dei pagamenti locali

Questo articolo descrive una soluzione per un problema noto in Adobe Commerce durante il pagamento, che si verifica quando viene visualizzato un messaggio di errore durante la selezione di un metodo di pagamento locale per alcuni paesi. Ciò si verifica per i paesi: Belgio, Italia, Paesi Bassi, Polonia e Spagna.

Il messaggio di errore &quot;*Non sono attualmente disponibili metodi di pagamento. Aggiorna l&#39;indirizzo di fatturazione.*&quot; apparirà, ma i metodi di pagamento locali continueranno ad apparire e funzioneranno correttamente. Una correzione permanente sarà disponibile in Adobe Commerce 2.4.1.

## Prodotti e versioni interessati

* Adobe Commerce on-premise 2.4.0
* Adobe Commerce sull’infrastruttura cloud 2.4.0

## Problema

<u>Prerequisiti</u>:

* Adobe Commerce 2.4.0 è installato.
* Crea un prodotto e una categoria.
* Configura [Metodo di pagamento Braintree](https://developer.adobe.com/commerce/webapi/graphql/payment-methods/braintree/).

<u>Passaggi da riprodurre</u>:

1. Passa alla vetrina.
1. Seleziona gli elementi da aggiungere al carrello.
1. Procedi con il pagamento.
1. Compila il modulo dell’indirizzo con un indirizzo valido.
1. Passare alla pagina Revisione e pagamenti.

<u>Risultato previsto</u>:

I metodi di pagamento locali dovrebbero essere visualizzati normalmente, senza un messaggio di errore.

<u>Risultato effettivo</u>:

Il messaggio di errore &quot;*Non sono attualmente disponibili metodi di pagamento. Aggiorna l&#39;indirizzo di fatturazione.*&quot; ma i metodi di pagamento locali continueranno a essere visualizzati e a funzionare correttamente.

## Soluzione

La soluzione consiste nell&#39;ignorare il messaggio di errore visualizzato e continuare con il pagamento come di consueto, in quanto tutti i metodi di pagamento locali funzioneranno normalmente. La correzione era disponibile a partire da Adobe Commerce versione 2.4.1.

## Lettura correlata

* [Problema noto di Adobe Commerce 2.4.0: i metodi di pagamento di Braintree non vengono visualizzati nell’estrazione di più indirizzi](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
