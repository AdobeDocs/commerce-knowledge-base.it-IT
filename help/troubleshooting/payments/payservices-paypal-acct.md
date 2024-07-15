---
title: Conto sandbox PayPal non verificato
description: Questo articolo spiega perché il tuo account sandbox PayPal per Payment Services potrebbe non essere verificato, impedendoti di completare l’onboarding in sandbox.
exl-id: 05ce130d-6dfe-4834-bdfc-837902100118
feature: Customer Service, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# Conto sandbox PayPal non verificato

Questo articolo spiega perché il tuo account sandbox PayPal per Payment Services potrebbe non essere verificato, impedendoti di completare l’onboarding in sandbox.

## Prodotti e versioni interessati

* [Payment Services](https://marketplace.magento.com/magento-payment-services.html) è ora compatibile con Adobe Commerce versioni da 2.4.0 a 2.4.4.

## Problema

Nella [documentazione sull&#39;onboarding](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/onboard.html) ti viene richiesto di iscriverti a un account PayPal, accedere al conto PayPal Developers e quindi creare un account sandbox. Se selezioni di creare un nuovo account durante l’onboarding nella finestra a comparsa per l’onboarding di PayPal, PayPal non sarà in grado di verificare il tuo account sandbox e non potrai completare l’onboarding.

<u>Passaggi da riprodurre</u>:

1. [installa Servizi di pagamento](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html) e [configura i servizi Commerce](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#configure-commerce-services).
1. Vai a **Servizi di pagamento** nell&#39;amministrazione e [avvia l&#39;onboarding della sandbox](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/onboard.html).
1. Nella finestra a comparsa per l&#39;onboarding di PayPal, puoi creare un nuovo account Business (invece di [accedere con un account sandbox PayPal creato in precedenza](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html#test-in-sandbox-environment) durante l&#39;onboarding.
1. Hai completato correttamente l’onboarding su PayPal.
1. L’Amministratore ti informa che i pagamenti sandbox sono in sospeso e che devi confermare il tuo indirizzo e-mail con PayPal per completare l’onboarding.

   Non hai ricevuto un&#39;email di conferma perché PayPal non è stato in grado di verificare il tuo indirizzo email.

## Causa

PayPal non sarà in grado di verificare il tuo account sandbox e non potrai completare l&#39;onboarding sandbox (il che significa che non puoi accettare pagamenti o testare la modalità sandbox) se crei il tuo account sandbox prima del tuo conto PayPal.

## Soluzione

1. Utilizzando un account sandbox creato nel portale [PayPal Developer](https://developer.paypal.com/docs/api-basics/sandbox/accounts/#create-a-business-sandbox-account).
1. Fai clic su [ripristina sandbox](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html#test-in-sandbox-environment) e riavvia l&#39;onboarding della sandbox.
1. [Contatta il supporto](mailto:payment-services-support@adobe.com) se non riesci ad alleviare i problemi dell&#39;account in modo da poter riprendere l&#39;onboarding e accettare i pagamenti.
