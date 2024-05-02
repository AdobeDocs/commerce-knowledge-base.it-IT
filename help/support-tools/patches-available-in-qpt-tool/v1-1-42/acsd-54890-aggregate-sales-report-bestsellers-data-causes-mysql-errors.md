---
title: '"ACSD-54890: cause "aggregate_sales_report_bestsellers_data" [!DNL MySQL] errori"'
description: Applica la patch ACSD-54890 per risolvere il problema Adobe Commerce che causa il "aggregate_sales_report_bestsellers_data" [!DNL MySQL] errori a causa di spazio insufficiente su `/tmpdisk`.
feature: Attributes
role: Admin, Developer
exl-id: 21a675dc-0750-4dc6-8cce-33e301f601bd
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---

# ACSD-54890 `aggregate_sales_report_bestsellers_data` causa errori MySQL

La patch ACSD-54890 risolve il problema in cui `aggregate_sales_report_bestsellers_data` cause [!DNL MySQL] errori dovuti a `/tmpdisk` spazio esaurito. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42. L’ID della patch è ACSD-54890. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il `aggregate_sales_report_bestsellers_data` cause **[!DNL MySQL]** errori dovuti a `/tmpdisk` spazio esaurito.

<u>Passaggi da riprodurre</u>:

Esegui il `aggregate_sales_report_bestsellers_data` processo cron quando `sales_bestsellers_aggregated_daily` La tabella contiene un&#39;enorme quantità di record, come decine di milioni di record.

<u>Risultati previsti</u>:

Nessun errore.

<u>Risultati effettivi</u>:

Si verifica il seguente errore:
`report.ERROR: Cron Job aggregate_sales_report_bestsellers_data has an error: SQLSTATE[HY000]: General error: 3 Error writing file '/tmp/#sql/fd=72' (Errcode: 28 "No space left on device")`

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
