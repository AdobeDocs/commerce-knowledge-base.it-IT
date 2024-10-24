---
title: "Adobe Commerce 2.4.0: eccezione durante l’installazione di B2B 1.2.0"
description: Questo articolo fornisce una correzione per un problema noto di Adobe Commerce relativo a un’eccezione generata durante "setup:upgrade" durante l’installazione di B2B 1.2.0.
exl-id: 2c1dadd9-7754-4b4c-8d37-b75c13beae5c
feature: B2B, Install, Upgrade
role: Developer
source-git-commit: a1046621259ea49eab74cd6ba3bba550e0c70283
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: eccezione durante l’installazione di B2B 1.2.0

Questo articolo fornisce una correzione per un problema noto di Adobe Commerce relativo a un&#39;eccezione generata durante `setup:upgrade` durante l&#39;installazione di B2B 1.2.0.

## Prodotti e versioni interessati

* Adobe Commerce on-premise 2.4.0
* Adobe Commerce sull’infrastruttura cloud 2.4.0
* B2B 1.2.0

## Problema

<u>Passaggi da riprodurre</u>

1. Installa Adobe Commerce quando è stato creato più di un archivio.
1. Crea un altro store.
1. Installare B2B 1.2.0.

>[!WARNING]
>
>È interessato anche l’aggiornamento di qualsiasi istanza B2B con più di 1 archivio da una versione precedente alla 1.2.0 o da un’istanza Commerce precedente alla 2.4.0.

<u>Risultato previsto</u>

Installazioni di B2B 1.2.0.

<u>Risultato effettivo</u>

Quando `setup:upgrade` viene eseguito per installare B2B 1.2.0, questo errore viene visualizzato nel modulo `PurchaseOrder`:

```php
Module 'Magento_PurchaseOrder':
  Unable to apply data patch Magento\PurchaseOrder\Setup\Patch\Data\InitPurchaseOrderSalesSequence
  for module Magento_PurchaseOrder. Original exception message: DDL statements
  are not allowed in transactions
```

## Soluzione

Applichi la patch fornita in questo articolo.

## Patch

La patch è allegata a questo articolo, disponibile per il download nei formati `.composer` e `.git` (dopo aver decompresso i file).

Per scaricarlo, scorri verso il basso fino alla fine dell’articolo e fai clic sul nome del file, oppure fai clic su uno dei seguenti collegamenti:

* [Patch compositore B2B-716\_compositore.patch](assets/B2B-716_composer.patch.zip)
* [Patch Git B2B-716\_git.patch](assets/B2B-716_git.patch.zip)

## Come applicare una patch

<u>Correzione compositore </u>

Consulta [Come applicare una patch del compositore fornita dall&#39;Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) per le istruzioni sulla patch del compositore.

<u>Patch Git </u>

* Per le istruzioni sulle patch Git per Adobe Commerce sull&#39;infrastruttura cloud, consulta [Applicare le patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.
* Per istruzioni sulla patch Git per Adobe Commerce, consulta [Applicazione delle patch: patch personalizzate](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#custom-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

* [Problema noto di Adobe Commerce 2.4.0: visualizzazione dei dati dei messaggi non elaborati nella vetrina](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Problema noto di Adobe Commerce 2.4.0: l’esportazione delle aliquote fiscali non funziona](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problema noto di Adobe Commerce 2.4.0: i metodi di pagamento Braintree non vengono visualizzati nel checkout di più indirizzi](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problema noto di Adobe Commerce 2.4.0: messaggio di errore durante la selezione del metodo di pagamento locale visualizzato per alcuni paesi durante l’acquisto](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Problema noto di Adobe Commerce 2.4.0: errore 404 durante la rimozione dei punti premio in caso di pagamento tramite multi-shipping](/help/troubleshooting/storefront/magento-2-4-0-404-error-removing-rewards-points-on-multi-shipping-checkout.md)
* [Problema noto di Adobe Commerce 2.4.0: errore di visualizzazione degli ordini](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [L’amministratore B2B di Adobe Commerce 2.4.0 non può aggiungere un prodotto configurabile all’offerta](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Problema noto di Adobe Commerce 2.4.0: l’aggiornamento delle attività del cliente non funziona](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Problema noto di Adobe Commerce 2.4.0: il pulsante &quot;Aggiungi selezioni al carrello&quot; non funziona](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
