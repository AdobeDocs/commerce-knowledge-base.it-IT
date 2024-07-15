---
title: "ACSD-55004: la convalida si blocca durante il caricamento di un file di importazione di dimensioni superiori al valore"
description: Applica la patch ACSD-55004 per risolvere il problema di Adobe Commerce in cui si verifica un arresto anomalo della convalida durante il caricamento di un file di importazione più grande del valore configurato in "php.ini".
feature: Data Import/Export
role: Admin, Developer
exl-id: 03b7667e-9b5b-4319-9135-dbc7fda7861d
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# ACSD-55004: la convalida si blocca durante il caricamento di un file di importazione di dimensioni superiori al valore

La patch ACSD-55004 risolve il problema relativo all&#39;arresto anomalo di una convalida durante il caricamento di un file di importazione di dimensioni superiori al valore configurato in `php.ini`. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.40. L’ID della patch è ACSD-55004. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La convalida si blocca durante il caricamento di un file di importazione di dimensioni superiori al valore configurato in `php.ini`.

<u>Passaggi da riprodurre</u>:

Provare a caricare un file di importazione di dimensioni superiori a quelle configurate in `php.ini`.

<u>Risultati previsti</u>:

La dimensione del file viene convalidata senza errori.

<u>Risultati effettivi</u>:

Arresto anomalo della convalida.

`var/log/exception.log` contiene:

```
[2023-10-06T21:36:30.470618+00:00] report.CRITICAL: Error: Class "Zend_Validate_File_Upload" not found in ../module-import-export/Model/Source/Upload.php:81
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
