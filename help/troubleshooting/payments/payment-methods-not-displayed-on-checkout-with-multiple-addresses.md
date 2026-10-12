---
title: Metodi di pagamento non visualizzati al momento del pagamento con più indirizzi
description: Questo articolo spiega che la maggior parte dei metodi di pagamento non vengono visualizzati al momento del pagamento quando vengono specificati più indirizzi di spedizione, perché la funzionalità è implementata solo per Cybersource.
exl-id: 68a9ee77-d0ef-43c5-9667-6d099b797666
feature: Checkout, Orders, Payments, Shipping/Delivery
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
  - id: 04d3134c-2afb-5bd7-ac14-e19fa935e848
    internal-label: Shipping/Delivery
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%
---
# Metodi di pagamento non visualizzati al momento del pagamento con più indirizzi

Questo articolo spiega che la maggior parte dei metodi di pagamento non vengono visualizzati al momento del pagamento quando vengono specificati più indirizzi di spedizione, perché la funzionalità è implementata solo per Cybersource.

## Prodotti e versioni interessati

* Adobe Commerce on-premise 2.x.x
* Adobe Commerce sull’infrastruttura cloud 2.x.x

>[!NOTE]
>
>L’integrazione del pagamento core Adobe Commerce Cybersource è obsoleta a partire dalla versione 2.3.3 e verrà completamente rimossa nella versione 2.4.0. Utilizza invece l&#39;[estensione ufficiale](https://marketplace.magento.com/cybersource-global-payment-management.html) da Marketplace.

## Problema

<u>Prerequisiti</u>: nell&#39;amministratore di Commerce, abilita e configura i metodi di pagamento PayPal e Cybersource e abilita Multishipping per il tuo archivio.

<u>Passaggi da riprodurre</u>:

1. Nella vetrina, aggiungi più prodotti al carrello.
1. Vai alla pagina del carrello.
1. Fare clic su **Estrai con più indirizzi**.
1. Accedi o crea un account.
1. Suddividere i prodotti tra gli indirizzi nella pagina Spedisci a più indirizzi.
1. Fare clic su **Vai alle informazioni sulla spedizione**.
1. Selezionare i metodi di spedizione per ogni spedizione.
1. Fai clic su **Continua con informazioni fatturazione**.

<u>Risultato previsto</u>: PayPal e Cybersource sono disponibili come opzioni di pagamento.

<u>Risultato effettivo</u>: solo Cybersource viene visualizzato come opzione di pagamento disponibile.

## Causa

Attualmente Cybersource è l’unico metodo di pagamento live supportato per il pagamento multishipping, a partire dalla versione 2.2.4. Il supporto per il multishipping sarà probabilmente creato per ogni metodo di pagamento uno per uno. Al momento non è possibile fornire date esatte o numeri di versione.
