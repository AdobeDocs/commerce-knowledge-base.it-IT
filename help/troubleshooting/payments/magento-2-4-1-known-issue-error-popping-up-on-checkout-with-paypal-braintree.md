---
title: 'Problema noto di Adobe Commerce 2.4.1: errore durante il pagamento con PayPal Braintree'
description: Questo articolo descrive un problema noto di Adobe Commerce 2.4.1, in cui un messaggio di errore compare e scompare nella fase di fatturazione di Pagamento se si utilizza il pagamento di Braintree PayPal e si seleziona la spedizione di più indirizzi.
exl-id: db3830b2-4885-4d89-85cd-bdcbd4b396e6
feature: Checkout, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Problema noto di Adobe Commerce 2.4.1: errore durante il pagamento con PayPal Braintree

Questo articolo descrive un problema noto di Adobe Commerce 2.4.1, in cui un messaggio di errore compare e scompare nella fase di fatturazione di Pagamento se si utilizza il pagamento di Braintree PayPal e si seleziona la spedizione di più indirizzi.

## Prodotti e versioni interessati

* Adobe Commerce sull’infrastruttura cloud 2.4.1
* Adobe Commerce on-premise 2.4.1

## Problema

Viene visualizzato un messaggio di errore e scompare nella fase di fatturazione di Pagamento se viene utilizzato il pagamento con Braintree PayPal e viene selezionata la spedizione di più indirizzi.

<u>Passaggi da riprodurre:</u>

1. Nella vetrina, accedi come cliente (facoltativamente potrebbe essere un pagamento come ospite, se abilitato in Amministrazione).
1. Aggiungi un prodotto al carrello.
1. Fai clic su per aprire l’anteprima del carrello.
1. Fare clic su **Visualizza e modifica carrello**.
1. Nella pagina del carrello, fai clic su **Estrai con più indirizzi**.
1. Fare clic su **Vai a Informazioni spedizione** e specificare gli indirizzi.
1. Fai clic su **Continua con informazioni fatturazione**.
1. Seleziona **Braintree PayPal** e fai clic sul pulsante **PayPal**.
1. Nella finestra popup, fai clic su **Accetto e paga**.

<u>Risultato previsto:</u>

L’ordine viene effettuato senza errori.

<u>Risultato effettivo:</u>

L’ordine viene effettuato, ma con un errore. Impossibile inizializzare l&#39;estrazione di *PayPal. Contattare il proprietario dell&#39;archivio*.  L&#39;errore viene visualizzato per un secondo e scompare.

## Correzione

Poiché il posizionamento dell’ordine non è bloccato, non è necessario eseguire i passaggi per una soluzione alternativa.
