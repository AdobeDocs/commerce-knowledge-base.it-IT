---
title: 2.3.4 Hotfix problema PayPal
description: Questo articolo fornisce una correzione per gli errori ricevuti durante il posizionamento dell'ordine quando si seleziona un'area in PayPal Express Checkout. Il problema è causato dalle modifiche apportate nella versione di Adobe Commerce v2.3.4 ed è correlato al modo in cui vengono analizzati i campi dell’indirizzo di pagamento PayPal Express.
exl-id: 9f5ec100-49b0-4ac5-8951-32b5c4fe6bed
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# 2.3.4 Hotfix problema PayPal

Questo articolo fornisce una correzione per gli errori ricevuti durante il posizionamento dell&#39;ordine quando si seleziona un&#39;area in PayPal Express Checkout. Il problema è causato dalle modifiche apportate nella versione di Adobe Commerce v2.3.4 ed è correlato al modo in cui vengono analizzati i campi dell’indirizzo di pagamento PayPal Express.

## Versioni e prodotti interessati

* Adobe Commerce sull’infrastruttura cloud v2.3.4
* Adobe Commerce on-premise v2.3.4

## Problema

Si verifica un errore durante l&#39;inserimento del paese e dell&#39;area geografica durante il posizionamento dell&#39;ordine in PayPal Express Checkout. Il problema è riproducibile per qualsiasi paese in cui il campo area nella sezione dell’indirizzo è un campo di testo (anziché un menu a discesa).

<u>Passaggi da riprodurre</u>:

1. Abilita Checkout PayPal Express.
1. Aggiungi il prodotto al carrello come ospite o quando hai effettuato l’accesso.
1. Vai al pagamento.
1. Seleziona l&#39;indirizzo di spedizione. Ad esempio, il *Regno Unito* . Immettere quindi un input nel campo **Stato/Provincia**. Ad esempio, *Nottinghamshire*.
1. Fai clic sul pulsante **Inserisci ordine** per effettuare l&#39;ordine. Ricevi una pagina di ordine e un’e-mail di conferma dell’ordine corrette.

<u>Risultato previsto:</u>

L’ordine è stato effettuato correttamente.

<u>Risultato effettivo:</u>

Quando si fa clic sul pulsante Ordine, viene visualizzato un errore:

```
Error 500: NOTICE: PHP message: PHP Fatal error: Uncaught Error: Call to a member
  function getId() on null in httpdocs/vendor/magento/module-paypal/Model/Api/Nvp.php:1527
```

## Soluzione

Per gli esercenti locali di Adobe Commerce: applica l&#39;[hotfix,](https://magento.com/tech-resources/download#download2353) disponibile nella sezione Download del portale [magento.com](https://magento.com) nel mio account.

Per i commercianti di infrastrutture cloud di Adobe Commerce: Adobe ha incluso la correzione nella versione 1.0.2 delle patch cloud per Commerce. Per istruzioni sull&#39;applicazione del pacchetto più recente, consulta le [note sulla versione delle patch cloud per Commerce](https://devdocs.magento.com/cloud/release-notes/mcp-release-notes.html?itm_source=devdocs&amp;itm_medium=quick_search&amp;itm_campaign=federated_search&amp;itm_term=cloud%20patche) nella documentazione per gli sviluppatori.

## Come applicare il cerotto

Per istruzioni, vedere [Come applicare una patch del compositore fornita dall&#39;Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) nella Knowledge Base di supporto.

## Lettura correlata

* [Informazioni sulla versione > Note sulla versione di Adobe Commerce 2.3.4 > Applica il problema PayPal Express Checkout con la patch dell&#39;area geografica per Adobe Commerce 2.3.4 per risolvere un problema critico di Checkout PayPal Express](https://devdocs.magento.com/guides/v2.3/release-notes/release-notes-2-3-4-commerce.html#apply-the-paypal-express-checkout-issue-with-region-patch-for-magento-234-to-address-a-critical-paypal-express-checkout-issue) nella documentazione per gli sviluppatori.
