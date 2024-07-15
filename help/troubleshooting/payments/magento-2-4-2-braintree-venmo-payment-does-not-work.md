---
title: "Adobe Commerce 2.4.2: il pagamento Braintree Venmo non funziona"
description: Questo articolo descrive un problema noto di Adobe Commerce 2.4.2 in cui non vengono generati ordini quando si utilizza Braintree Venmo durante il pagamento. Al momento non è disponibile alcuna risoluzione.
exl-id: 1832ab64-5024-444b-915e-473b34979a6e
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '205'
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

L’ordine viene creato in Adobe Commerce dopo che il cliente viene reindirizzato allo store dall’app Venmo e creato in Braintree, come previsto.

## Soluzione

Al momento non è disponibile alcuna risoluzione.
