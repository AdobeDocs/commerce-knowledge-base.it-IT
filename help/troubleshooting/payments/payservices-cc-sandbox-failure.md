---
title: Pagamenti con carta di credito non riusciti in un ambiente Sandbox
description: Questo articolo spiega perché una carta di credito di test non riesce in un ambiente Sandbox con API PayPal.
exl-id: 65fd08e0-eefc-47f3-8964-bef3610e6182
feature: Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---

# Pagamenti con carta di credito non riusciti in un ambiente Sandbox

Questo articolo spiega perché una carta di credito di test non riesce in un ambiente Sandbox con API PayPal.

## Prodotti e versioni interessati


* Adobe Commerce 2.4.0 - 2.4.4 , tutte le opzioni di implementazione, con [Servizi di pagamento](https://marketplace.magento.com/magento-payment-services.html)

## Problema

Quando si utilizza una carta di credito Visa di prova `4111 1111 1111 1111` da PayPal, a volte non riesce a causa dei criteri di frode PayPal con il seguente errore:

```terminal
Error happened when processing the request. Please try again later.
```

## Causa

Questo errore viene visualizzato quando PayPal contrassegna un numero di carta di credito di test specifico per la frode. Questo accade perché si tratta di un numero di carta di credito di prova utilizzato da tutti in tutto il mondo per i test con le API PayPal.

## Soluzione

Utilizza un&#39;altra carta di credito di prova. Per generare carte di credito fittizie è possibile utilizzare per il test:

1. Vai al portale per sviluppatori PayPal [Generatore carta di credito](https://developer.paypal.com/developer/creditCardGenerator/) pagina.
1. Accedi al dashboard di PayPal Developer Portal.
1. Genera una carta di credito di prova.
