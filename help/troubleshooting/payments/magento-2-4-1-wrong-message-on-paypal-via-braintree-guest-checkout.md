---
title: 'Adobe Commerce 2.4.1: messaggio errato al pagamento PayPal-Braintree'
description: Questo articolo descrive un problema noto di Adobe Commerce 2.4.1 in cui se il pagamento dei clienti guest è disabilitato, un cliente ospite che tenta di effettuare un ordine con PayPal tramite Braintree riceve un messaggio di errore non informativo.
exl-id: 758f5c57-997e-4aca-b299-9934c94fa121
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
source-wordcount: '408'
ht-degree: 0%
---
# Adobe Commerce 2.4.1: messaggio errato al pagamento PayPal-Braintree

Questo articolo descrive un problema noto di Adobe Commerce 2.4.1 in cui se il pagamento dei clienti guest è disabilitato, un cliente ospite che tenta di effettuare un ordine con PayPal tramite Braintree riceve un messaggio di errore non informativo.

## Prodotti e versioni interessati

* Adobe Commerce on-premise 2.4.0, 2.4.1
* Adobe Commerce sull’infrastruttura cloud 2.4.0, 2.4.1

## Problema

Viene visualizzato un errore non specifico quando il pagamento del cliente ospite viene disabilitato dal backend e l&#39;opzione di pagamento PayPal tramite Braintree viene selezionata dal Mini-carrello o dal Carrello acquisti.

<u>Prerequisiti</u>:

1. In Amministrazione Commerce, in **Archivi** > **Configurazione** > **Vendite** > **Pagamento**, impostare **Consenti pagamento ospite** = *No*.
1. Abilita PayPal tramite Braintree come descritto in [Braintree](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/payments/braintree?) nella nostra guida utente.

<u>Passaggi da riprodurre</u>:

1. Aggiungi prodotto al carrello come ospite.
1. Seleziona **Mini-carrello** e fai clic su **Paga con PayPal**.
1. Completa l&#39;estrazione di Paypal, quindi arriverai alla pagina di revisione dell&#39;ordine.
1. Selezionare **Metodo di spedizione**.
1. Fai clic su **Inserisci ordine**.

<u>Risultati previsti</u>:

Quando un cliente fa clic sul pulsante PayPal sulla pagina Mini-carrello o Carrello acquisti, deve essere visualizzato il seguente messaggio:

<pre><code class="language-bash">To check out, please sign in with your email address.</code></pre>

Se abiliti Paypal diretto senza utilizzare Braintree, questo scenario si comporta in modo diverso. Non consente all&#39;utente ospite di continuare il processo di pagamento. Quando l&#39;utente ospite fa clic sul pulsante PayPal nel Mini-carrello, viene visualizzato il seguente messaggio:

<pre><code class="language-bash">To check out, please sign in with your email address.</code></pre>

<u>Risultati effettivi</u>:

Il cliente viene reindirizzato alla pagina Carrello acquisti e viene visualizzato il seguente messaggio:

<pre><code class="language-bash">The customer email is missing. Enter and try again.</code></pre>

## Soluzione alternativa

La soluzione a questo problema consiste nel fatto che il cliente può effettuare l’accesso in uno store (gli utenti connessi non utilizzano il pagamento come ospite). in cui l&#39;estrazione guest è disabilitata. Questo problema è stato risolto nella versione 2.4.2 di Adobe Commerce.

## Lettura correlata

* [Procedure consigliate per il numero di prodotti nel carrello in Adobe Commerce](https://support.magento.com/hc/en-us/articles/360048550332) nella Knowledge Base di supporto.
* [Tutorial sull&#39;elaborazione dell&#39;ordine: passaggio 1. Aggiungi elementi al carrello](https://developer.adobe.com/commerce/webapi/rest/tutorials/orders/order-add-items/) nella documentazione per gli sviluppatori
* [Tutorial sull&#39;estrazione di GraphQL: passaggio 1. Aggiungi prodotti al carrello](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/add-product-to-cart/) nella documentazione per gli sviluppatori
