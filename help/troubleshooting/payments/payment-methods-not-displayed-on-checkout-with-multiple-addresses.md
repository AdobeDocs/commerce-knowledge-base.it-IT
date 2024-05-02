---
title: Metodi di pagamento non visualizzati al momento del pagamento con più indirizzi
description: Questo articolo spiega che la maggior parte dei metodi di pagamento non vengono visualizzati al momento del pagamento quando vengono specificati più indirizzi di spedizione, perché la funzionalità è implementata solo per Cybersource.
exl-id: 68a9ee77-d0ef-43c5-9667-6d099b797666
feature: Checkout, Orders, Payments, Shipping/Delivery
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# Metodi di pagamento non visualizzati al momento del pagamento con più indirizzi

Questo articolo spiega che la maggior parte dei metodi di pagamento non vengono visualizzati al momento del pagamento quando vengono specificati più indirizzi di spedizione, perché la funzionalità è implementata solo per Cybersource.

## Prodotti e versioni interessati

* Adobe Commerce on-premise 2.x.x
* Adobe Commerce sull’infrastruttura cloud 2.x.x

>[!NOTE]
>
>L’integrazione del pagamento core Adobe Commerce Cybersource è obsoleta a partire dalla versione 2.3.3 e verrà completamente rimossa nella versione 2.4.0. Utilizza il [estensione ufficiale](https://marketplace.magento.com/cybersource-global-payment-management.html) dal marketplace.

## Problema

<u>Prerequisiti</u>: in Commerce Admin, abilita e configura i metodi di pagamento PayPal e Cybersource e abilita Multishipping per il tuo store.

<u>Passaggi da riprodurre</u>:

1. Nella vetrina, aggiungi più prodotti al carrello.
1. Vai alla pagina del carrello.
1. Clic **Check-Out con più indirizzi**.
1. Accedi o crea un account.
1. Suddividere i prodotti tra gli indirizzi nella pagina Spedisci a più indirizzi.
1. Clic **Vai a Informazioni spedizione**.
1. Selezionare i metodi di spedizione per ogni spedizione.
1. Clic **Continua con le informazioni di fatturazione**.

<u>Risultato previsto</u>: PayPal e Cybersource sono disponibili come opzioni di pagamento.

<u>Risultato effettivo</u>: solo Cybersource viene visualizzato come opzione di pagamento disponibile.

## Causa

Attualmente Cybersource è l’unico metodo di pagamento live supportato per il pagamento multishipping, a partire dalla versione 2.2.4. Il supporto per il multishipping sarà probabilmente creato per ogni metodo di pagamento uno per uno. Al momento non è possibile fornire date esatte o numeri di versione.
