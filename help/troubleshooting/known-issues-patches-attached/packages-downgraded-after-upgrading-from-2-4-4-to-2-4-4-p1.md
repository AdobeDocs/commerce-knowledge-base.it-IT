---
title: Pacchetti declassati dopo l’aggiornamento da 2.4.4 a 2.4.4-p1
description: Questo articolo fornisce un hotfix per il problema quando i commercianti nella versione 2.4.4 eseguono il comando "compositore update" (aggiornamento compositore) e poi i pacchetti (moduli) elencati di seguito vengono scaricati alle versioni precedenti che non sono compatibili con la versione 2.4.4 e che devono essere utilizzati solo con la versione 2.4.5 e successive.
exl-id: 4ebdbcd7-6905-4647-b071-1e4413455f38
feature: Upgrade
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 0%

---

# Pacchetti declassati dopo l’aggiornamento da 2.4.4 a 2.4.4-p1

Questo articolo fornisce un hotfix per il problema che si verifica quando gli esercenti eseguono la versione 2.4.4 di `composer update` e quindi i pacchetti (moduli) elencati di seguito vengono scaricati alle versioni precedenti che non sono compatibili con la versione 2.4.4 e che devono essere utilizzati solo con la versione 2.4.5 e successive.

## Prodotti e versioni interessati

* Adobe Commerce sull’infrastruttura cloud 2.4.4
* Adobe Commerce on-premise 2.4.4
* Magento Open Source 2.4.4

## Problema

Esistono due scenari in cui questo problema può verificarsi e come può essere riprodotto:

### Scenario 1

<u>Passaggi da riprodurre</u>:

Quando si esegue l’aggiornamento da 2.4.4 a 2.4.4-p1, vi è una serie di pacchetti (moduli) che vengono declassati con output simile:

```text
Downgrading magento/module-adobe-ims (2.1.4 => 2.1.3)
Downgrading magento/module-adobe-ims-api (2.1.2 => 2.1.1)
Downgrading magento/module-adobe-stock-admin-ui (1.3.2 => 1.3.1)
Downgrading magento/module-adobe-stock-client-api (2.1.2 => 2.1.1)
Downgrading magento/module-adobe-stock-image (1.3.3 => 1.3.2)
Downgrading magento/module-adobe-stock-image-admin-ui (1.3.3 => 1.3.2)
Downgrading magento/module-banner-page-builder (2.2.3 => 2.2.2)
Downgrading magento/module-inventory (1.2.3 => 1.2.2)
Downgrading magento/module-inventory-admin-ui (1.2.3 => 1.2.2-p1)
Downgrading magento/module-inventory-advanced-checkout (1.2.2 => 1.2.1)
Downgrading magento/module-inventory-api (1.2.3 => 1.2.2-p1)
Downgrading magento/module-inventory-bundle-product (1.2.2 => 1.2.1)
Downgrading magento/module-inventory-catalog-api (1.3.3 => 1.3.2)
Downgrading magento/module-inventory-configurable-product-admin-ui (1.2.3 => 1.2.2-p1)
Downgrading magento/module-inventory-configurable-product-frontend-ui (1.0.3 => 1.0.2)
Downgrading magento/module-inventory-import-export (1.2.3 => 1.2.2)
Downgrading magento/module-inventory-in-store-pickup-admin-ui (1.1.2 => 1.1.1)
Downgrading magento/module-inventory-in-store-pickup-frontend (1.1.3 => 1.1.2)
Downgrading magento/module-inventory-in-store-pickup-graph-ql (1.1.2 => 1.1.1)
Downgrading magento/module-inventory-in-store-pickup-sales-admin-ui (1.1.3 => 1.1.2-p1)
Downgrading magento/module-inventory-in-store-pickup-shipping (1.1.2 => 1.1.1)
Downgrading magento/module-inventory-low-quantity-notification (1.2.2 => 1.2.1)
Downgrading magento/module-inventory-low-quantity-notification-api (1.2.2 => 1.2.1-p1)
Downgrading magento/module-inventory-requisition-list (1.2.3 => 1.2.2)
Downgrading magento/module-inventory-sales-admin-ui (1.2.3 => 1.2.2)
Downgrading magento/module-inventory-sales-api (1.2.2 => 1.2.1)
Downgrading magento/module-inventory-shipping-admin-ui (1.2.3 => 1.2.2-p1)
Downgrading magento/module-inventory-source-selection-api (1.4.2 => 1.4.1-p1)
Downgrading magento/module-inventory-wishlist (1.0.2 => 1.0.1)
Downgrading magento/module-page-builder (2.2.3 => 2.2.2)
Downgrading magento/module-re-captcha-checkout-sales-rule (1.1.1 => 1.1.0)
Downgrading magento/module-re-captcha-customer (1.1.3 => 1.1.2)
Downgrading magento/module-re-captcha-frontend-ui (1.1.3 => 1.1.2)
Downgrading magento/module-staging-page-builder (2.2.3 => 2.2.2)
Downgrading magento/module-two-factor-auth (1.1.4 => 1.1.3)
Removing magento/module-admin-adobe-ims (100.4.0)
```

<u>Risultati previsti</u>:

L’aggiornamento dalla versione 2.4.4 alla versione 2.4.4-p1 genera i pacchetti (moduli) corretti per la versione 2.4.4-p1.

<u>Risultati effettivi</u>:

Durante l’aggiornamento dalla versione 2.4.4 alla versione 2.4.4-p1, le versioni di questi pacchetti (moduli) vengono downgrade, ma è possibile ignorare questi messaggi e non influire sulle funzionalità.

### Scenario 2

<u>Passaggi da riprodurre</u>:

Quando i commercianti della versione 2.4.4 eseguono `composer update` , quindi gli stessi pacchetti (moduli) elencati sopra in **Scenario 1** vengono aggiornati alle versioni più recenti, compatibili solo con la versione 2.4.5 e non destinate all’utilizzo con la versione 2.4.4.

<u>Risultati previsti</u>:

L’aggiornamento dalla versione 2.4.4 alla versione 2.4.4-p1 genera i pacchetti (moduli) corretti per la versione 2.4.4-p1.

<u>Risultati effettivi</u>:

I pacchetti (moduli) vengono declassati dopo l’aggiornamento dalla versione 2.4.4 alla versione 2.4.4-p1.

## Soluzione 1: patch

La patch è allegata a questo articolo. Per scaricarlo, scorri verso il basso fino alla fine dell’articolo e fai clic sul nome del file o sul seguente collegamento: [Scarica ACPLTSRV-2017-fix.sh.zip](assets/ACPLTSRV-2017-fix.sh.zip)

## Versioni compatibili di Adobe Commerce e Magento Open Source:

La patch è stata creata per:

* Adobe Commerce sull’infrastruttura cloud 2.4.4
* Adobe Commerce on-premise 2.4.4
* Magento Open Source 2.4.4

>[!NOTE]
>
>La patch non è compatibile con altre versioni ed edizioni di Adobe Commerce e di Magento Open Source.

## Come applicare il cerotto

Utilizza lo script di base allegato [ACPLTSRV-2017-fix.sh.zi p](assets/ACPLTSRV-2017-fix.sh.zip) come soluzione alternativa per questo problema.

**Istruzioni precise su come utilizzare lo script:**

### In Adobe Commerce sull’infrastruttura cloud:

1. Scaricare il file script di base `ACPLTSRV-2017-fix.sh` al pagamento locale della base di codice cloud.
1. Eseguire il file di script di base `ACPLTSRV-2017-fix.sh` per modificare localmente i file del compositore.
1. Aggiungi e conferma i file del compositore modificati nel tuo archivio Git.

### Su Adobe Commerce o Magento Open Source on-premise:

1. Posiziona lo script Bash `ACPLTSRV-2017-fix.sh` nel `root` cartella dell’installazione di Adobe Commerce/Magento Open Source 2.4.4 (la stessa cartella del file `composer.json`).
1. Esegui lo script Bash con un `apply` argomento per bloccare i pacchetti interessati (moduli) alle rispettive versioni 2.4.4:

   ```bash
   sh ACPLTSRV-2017-fix.sh apply
   ```

1. Esegui il compositore aggiornato per installare i pacchetti (moduli) bloccati.
1. Quando sei pronto per eseguire l’aggiornamento a 2.4.5 o 2.4.4-p1, esegui lo script con `rollback` argomento:

   ```bash
   sh ACPLTSRV-2017-fix.sh rollback
   ```

   Se si ignora questo passaggio, si verificheranno errori di aggiornamento a causa di pacchetti (moduli) in conflitto tra loro.
1. Dopo aver completato i passaggi precedenti, puoi iniziare l’aggiornamento.

## Soluzione alternativa 2

La seconda soluzione per questo problema consiste nel non eseguire `composer update` senza argomenti.
