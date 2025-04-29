---
title: Problema di prestazioni nell’aggiornamento del modulo Magento_Company dopo l’aggiornamento B2B 1.5.2
description: Questo articolo fornisce un hotfix per il problema di prestazioni nell’aggiornamento del modulo Magento_Company dopo l’aggiornamento B2B 1.5.2, affrontando il problema dei tempi di elaborazione eccessivamente lunghi per i set di dati di grandi dimensioni nella tabella company_structure.
feature: B2B, Upgrade
role: Admin, Developer
source-git-commit: d06f0045b4c4c1615bd3abec963eb17fdee93860
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# Problema di prestazioni nell’aggiornamento del modulo Magento_Company dopo l’aggiornamento B2B 1.5.2

Questo articolo fornisce un hotfix per il problema di prestazioni nell&#39;aggiornamento del modulo `Magento_Company` dopo l&#39;aggiornamento B2B 1.5.2, risolvendo il problema dei tempi di elaborazione eccessivamente lunghi per set di dati di grandi dimensioni (oltre 100.000 record) nella tabella `company_structure`.

## Prodotti e versioni interessati

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-px + B2B 1.5.2
* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-px + B2B 1.5.2
* Adobe Commerce (tutti i metodi di implementazione) 2.4.8 + B2B 1.5.2

## Problema

L&#39;aggiornamento del modulo `Magento_Company` dopo l&#39;aggiornamento a B2B 1.5.2 richiede un tempo eccessivo quando si elabora un numero elevato di record (~100.000+) nella tabella `company_structure`.

<u>Prerequisiti</u>:

* È necessario installare ACSD-65540_B2B_1.5.2.patch.
* Adobe Commerce 2.4.6 - 2.4.8
* B2B versione 1.5.0, 1.5.1 o B2B versione 1.5.2 con la patch ACSD-65540 applicata

<u>Passaggi da riprodurre</u>:

1. Assegnare una società a una società padre per stabilire la gerarchia della società. Per ulteriori informazioni, consulta [Gestire la gerarchia aziendale](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/company-management/manage-company-hierarchy) nella guida B2B di Adobe Commerce.
1. Aggiornamento B2B alla versione 1.5.2.

<u>Risultati previsti</u>:

Aggiornamento completato correttamente.

<u>Risultati effettivi</u>:

L&#39;aggiornamento del modulo `Magento_Company` richiede molto tempo se la tabella `company_structure` contiene molti record.

## Soluzione

Per risolvere il problema, effettua le seguenti operazioni:

1. Aggiornare il modulo B2B alla versione 1.5.2:

   ```
   composer require magento/module-b2b:1.5.2 --no-update
   composer update magento/module-b2b
   ```

1. Applica [ACSD-65540_B2B_1.5.2.patch](/help/troubleshooting/installation-and-upgrade/assets/ACSD-65540_B2B_1.5.2.zip).

1. Applica il [ACSD-65540_B2B_1.5.2_DEPENDENT_ACSD-65684_B2B_1.5.2.patch](/help/troubleshooting/installation-and-upgrade/assets/ACSD-65540_B2B_1.5.2_DEPENDENT_ACSD-65684_B2B_1.5.2.patch.zip) allegato.
1. Esegui `bin/magento setup:upgrade` dopo l&#39;applicazione della patch.

### Come applicare il cerotto

Decomprimi il file e vedi [Come applicare una patch del compositore fornita da Adobe](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento) nella Knowledge Base di supporto per le istruzioni.

### Applicare una patch utilizzando le patch cloud

Per gli esercenti di Adobe Commerce on Cloud, segui i passaggi seguenti:

1. Aggiorna la versione del modulo cloud-patches alla 1.1.5 per installare la patch ACSD-65540_B2B_1.5.2.patch distribuita come MCLOUD-13605.

   >[!NOTE]
   >
   >Per verificare se la patch è già installata, eseguire le operazioni riportate di seguito.
   > `./vendor/bin/magento-patches -n status | grep MCLOUD-13605`

   ```
   composer require magento/magento-cloud-patches:1.1.5 --no-update
   composer update magento/magento-cloud-patches
   ```

1. Aggiungere ACSD-65540_B2B_1.5.2_DEPENDENT_ACSD-65684_B2B_1.5.2.patch alla directory `m2-hotfixes`.
1. Eseguire il commit e il push delle modifiche per avviare la ridistribuzione e `bin/magento setup:upgrade`. Per istruzioni, consulta [Applicare le patch](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida di Adobe Commerce su Cloud.

## Lettura correlata

* [L&#39;aggiornamento a B2B 1.5.2 non riesce e viene restituito un errore di sintassi SQL a causa della mancanza della funzione REGEXP_LIKE](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/sql-syntax-error-due-to-missing-regexp-like-function)
