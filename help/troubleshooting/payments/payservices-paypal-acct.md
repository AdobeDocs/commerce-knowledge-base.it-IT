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

* [Servizi di pagamento](https://marketplace.magento.com/magento-payment-services.html) è ora compatibile con Adobe Commerce versioni da 2.4.0 a 2.4.4.

## Problema

Nostro [documentazione sull’onboarding](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/onboard.html) indica di iscriversi a un conto PayPal, di accedere al conto PayPal Developers e quindi di creare un conto sandbox. Se selezioni di creare un nuovo account durante l’onboarding nella finestra a comparsa per l’onboarding di PayPal, PayPal non sarà in grado di verificare il tuo account sandbox e non potrai completare l’onboarding.

<u>Passaggi da riprodurre</u>:

1. Tu [installare Payment Services](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html) e [configurare i servizi Commerce](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#configure-commerce-services).
1. Vai a **Servizi di pagamento** in Admin e [avviare l’onboarding della sandbox](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/onboard.html).
1. Nella finestra a comparsa per l&#39;onboarding di PayPal che viene visualizzata, puoi creare un nuovo account Business (anziché [effettuare l&#39;accesso con un account sandbox PayPal creato in precedenza](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html#test-in-sandbox-environment) durante l’onboarding.
1. Hai completato correttamente l’onboarding su PayPal.
1. L’Amministratore ti informa che i pagamenti sandbox sono in sospeso e che devi confermare il tuo indirizzo e-mail con PayPal per completare l’onboarding.

   Non hai ricevuto un&#39;email di conferma perché PayPal non è stato in grado di verificare il tuo indirizzo email.

## Causa

PayPal non sarà in grado di verificare il tuo account sandbox e non potrai completare l&#39;onboarding sandbox (il che significa che non puoi accettare pagamenti o testare la modalità sandbox) se crei il tuo account sandbox prima del tuo conto PayPal.

## Soluzione

1. Utilizzo di un account sandbox creato in [PayPal Developer](https://developer.paypal.com/docs/api-basics/sandbox/accounts/#create-a-business-sandbox-account) Portale.
1. Clic [ripristina sandbox](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html#test-in-sandbox-environment) e riavvia l’onboarding della sandbox.
1. [Contatta il supporto](mailto:payment-services-support@adobe.com) se non riesci ad alleviare i problemi dell’account in modo da poter riprendere l’onboarding e accettare i pagamenti.
