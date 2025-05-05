---
title: L’aggiornamento a B2B 1.5.2 non riesce e viene restituito un errore di sintassi SQL a causa della mancanza della funzione REGEXP_LIKE
description: Questo articolo fornisce un hotfix per il problema in cui si verifica un errore di sintassi SQL dovuto alla funzione REGEXP_LIKE mancante durante il tentativo di aggiornamento della tabella company_structure.
feature: B2B, Upgrade
role: Admin, Developer
exl-id: c5fe316c-99e3-482e-80b5-25aaae371230
source-git-commit: 04e17dfdf143e233eb2767064c1328990c899eda
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# L’aggiornamento a B2B 1.5.2 non riesce e viene restituito un errore di sintassi SQL a causa della mancanza della funzione REGEXP_LIKE

>[!INFO]
>
>Se si verifica un problema di prestazioni durante l&#39;aggiornamento del modulo `Magento_Company` dopo l&#39;aggiornamento a B2B 1.5.2, applicare il [ACSD-65540_B2B_1.5.2_DEPENDENT_ACSD-65684_B2B_1.5.2.patch allegato](assets/ACSD-65540_B2B_1.5.2_DEPENDENT_ACSD-65684_B2B_1.5.2.patch.zip).
>
>Per ulteriori informazioni, consultare [Problema di prestazioni nell&#39;aggiornamento del modulo Magento_Company dopo l&#39;aggiornamento B2B 1.5.2](/help/troubleshooting/installation-and-upgrade/magento-company-module-upgrade-performance-issue.md) nella Knowledge Base di Adobe Commerce.

In questo articolo viene fornito un hotfix per l&#39;errore di sintassi SQL che si verifica a causa della funzione `REGEXP_LIKE` mancante durante il tentativo di aggiornamento della tabella `company_structure`.

## Prodotti e versioni interessati

* Adobe Commerce (tutti i metodi di distribuzione) 2.4.6-px + B2B 1.5.2 utilizzando [!DNL MariaDB] 10.6
* Adobe Commerce (tutti i metodi di distribuzione) 2.4.7-px + B2B 1.5.2 utilizzando [!DNL MariaDB] 10.6

## Problema

L&#39;aggiornamento alla versione 1.5.2 del B2B non riesce e si verifica un errore di sintassi SQL a causa della mancanza della funzione `REGEXP_LIKE` durante il tentativo di aggiornare la tabella `company_structure`.

<u>Prerequisiti</u>:

* MariaDB 10,6
* Adobe Commerce 2.4.6x o 2.4.7x
* B2B versione 1.5.0 o 1.5.1

<u>Passaggi da riprodurre</u>:

1. Assegnare una società a una società padre per stabilire la gerarchia della società. Per ulteriori informazioni, consulta [Gestire la gerarchia aziendale](https://experienceleague.adobe.com/it/docs/commerce-admin/b2b/company-management/manage-company-hierarchy) nella guida B2B di Adobe Commerce.
1. Aggiornamento B2B alla versione 1.5.2.

<u>Risultati previsti</u>:

Aggiornamento completato correttamente.

<u>Risultati effettivi</u>:

`bin/magento setup:upgrade` ha esito negativo con il seguente errore:

```
Unable to apply data patch Magento\Company\Setup\Patch\Data\SetCompanyForStructure for module Magento_Company. Original exception message: SQLSTATE[42000]: Syntax error or access violation: 1305 FUNCTION REGEXP_LIKE does not exist, query was: UPDATE `company_structure` SET `company_id` = ? WHERE (REGEXP_LIKE(path, '^123(/.+)?$'))
```

## Soluzione

Per risolvere il problema, effettua le seguenti operazioni:

1. Aggiornare il modulo B2B alla versione 1.5.2:

   ```
   composer require magento/module-b2b:1.5.2 --no-update
   composer update magento/module-b2b
   ```

1. Applica la patch [ACSD-65540_B2B_1.5.2.zip](assets/ACSD-65540_B2B_1.5.2.zip) allegata. Per istruzioni, consulta [Come applicare una patch del compositore fornita da Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) nella Knowledge Base di supporto.
1. Esegui `bin/magento setup:upgrade`.

### Applicare una patch utilizzando le patch cloud

Per l’infrastruttura Adobe Commerce on Cloud, segui i passaggi seguenti:

1. Aggiornare la versione del modulo `cloud-patches` alla versione 1.1.5:

   ```
   composer require magento/magento-cloud-patches:1.1.5 --no-update
   composer update magento/magento-cloud-patches
   ```

1. Esegui il commit e invia le modifiche per avviare la ridistribuzione. Per istruzioni, consulta [Applicare le patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida di Adobe Commerce su Cloud.
