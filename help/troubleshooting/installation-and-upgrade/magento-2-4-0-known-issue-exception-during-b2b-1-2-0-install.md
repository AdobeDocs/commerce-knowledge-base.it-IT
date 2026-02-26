---
title: 'Adobe Commerce 2.4.0: eccezione durante l’installazione di B2B 1.2.0'
description: Questo articolo fornisce una correzione per un problema noto di Adobe Commerce relativo a un’eccezione generata durante "setup:upgrade" durante l’installazione di B2B 1.2.0.
exl-id: 2c1dadd9-7754-4b4c-8d37-b75c13beae5c
feature: B2B, Install, Upgrade
role: Developer
source-git-commit: 7705b6030d2f0877c228dae1707916ad38c9d587
workflow-type: tm+mt
source-wordcount: '305'
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

Per istruzioni sulla patch del compositore, vedere [Come applicare una patch del compositore fornita da Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md).

<u>Patch Git </u>

* Per le istruzioni sulle patch Git per Adobe Commerce sull&#39;infrastruttura cloud, consulta [Applicare le patch](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.
* Per istruzioni sulla patch Git per Adobe Commerce, consulta [Applicazione delle patch: patch personalizzate](https://experienceleague.adobe.com/it/docs/commerce-operations/upgrade-guide/patches/overview#custom-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

* [Problema noto di Adobe Commerce 2.4.0: i metodi di pagamento di Braintree non vengono visualizzati nell’estrazione di più indirizzi](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problema noto di Adobe Commerce 2.4.0: messaggio di errore durante la selezione del metodo di pagamento locale visualizzato per alcuni paesi durante l’acquisto](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
