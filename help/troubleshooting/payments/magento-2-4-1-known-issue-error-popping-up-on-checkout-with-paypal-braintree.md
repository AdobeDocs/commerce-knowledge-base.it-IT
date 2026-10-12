---
title: 'Adobe Commerce 2.4.1 problema noto: errore durante il pagamento con PayPal Braintree'
description: Questo articolo descrive un problema noto di Adobe Commerce 2.4.1, in cui un messaggio di errore compare e scompare nella fase di fatturazione di Pagamento se si utilizza il pagamento PayPal Braintree e si seleziona la spedizione di più indirizzi.
exl-id: db3830b2-4885-4d89-85cd-bdcbd4b396e6
feature: Checkout, Orders, Payments
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
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 0%
---
# Adobe Commerce 2.4.1 problema noto: errore durante il pagamento con PayPal Braintree

Questo articolo descrive un problema noto di Adobe Commerce 2.4.1, in cui un messaggio di errore compare e scompare nella fase di fatturazione di Pagamento se si utilizza il pagamento PayPal Braintree e si seleziona la spedizione di più indirizzi.

## Prodotti e versioni interessati

* Adobe Commerce sull’infrastruttura cloud 2.4.1
* Adobe Commerce on-premise 2.4.1

## Problema

Viene visualizzato un messaggio di errore e scompare nella fase di fatturazione di Pagamento se viene utilizzato il pagamento PayPal Braintree e sono selezionati più indirizzi di spedizione.

<u>Passaggi da riprodurre:</u>

1. Nella vetrina, accedi come cliente (facoltativamente potrebbe essere un pagamento come ospite, se abilitato in Amministrazione).
1. Aggiungi un prodotto al carrello.
1. Fai clic su per aprire l’anteprima del carrello.
1. Fare clic su **Visualizza e modifica carrello**.
1. Nella pagina del carrello, fai clic su **Estrai con più indirizzi**.
1. Fare clic su **Vai a Informazioni spedizione** e specificare gli indirizzi.
1. Fai clic su **Continua con informazioni fatturazione**.
1. Seleziona **PayPal Braintree** e fai clic sul pulsante **PayPal**.
1. Nella finestra popup, fai clic su **Accetto e paga**.

<u>Risultato previsto:</u>

L’ordine viene effettuato senza errori.

<u>Risultato effettivo:</u>

L’ordine viene effettuato, ma con un errore. Impossibile inizializzare l&#39;estrazione di *PayPal. Contattare il proprietario dell&#39;archivio*.  L&#39;errore viene visualizzato per un secondo e scompare.

## Correzione

Poiché il posizionamento dell’ordine non è bloccato, non è necessario eseguire i passaggi per una soluzione alternativa.
