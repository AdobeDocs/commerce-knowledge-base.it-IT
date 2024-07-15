---
title: "ACSD-53628: il rapporto ordine cliente CSV mostra caratteri speciali non corretti"
description: Applicare la patch ACSD-53628 per risolvere il problema Adobe Commerce relativo alla visualizzazione di caratteri speciali non corretti nel rapporto ordine cliente CSV.
feature: Orders, Data Import/Export
role: Admin, Developer
exl-id: d898fdb8-cab9-49ab-ad8e-43feadf49aa0
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# ACSD-53628: il rapporto ordine cliente CSV mostra caratteri speciali non corretti

La patch ACSD-53628 risolve il problema relativo alla visualizzazione di caratteri speciali non corretti nel rapporto CSV degli ordini di vendita. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.37. L’ID della patch è ACSD-53628. Il problema è stato risolto in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione): 2.4.5-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione): 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il rapporto CSV ordini cliente contiene caratteri speciali non corretti.

<u>Passaggi da riprodurre</u>:

1. Modificare **[!UICONTROL Base Currency]** e **[!UICONTROL Default Display Currency]** in euro nella configurazione della valuta.
1. Effettua un ordine.
1. Nella barra laterale di amministrazione, vai a **[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Seleziona le date. Fare clic su **[!UICONTROL Show Report]**. Fare clic su **[!UICONTROL Export]** per esportare il file CSV.

<u>Risultati previsti</u>:

I caratteri speciali in un file CSV esportato vengono visualizzati correttamente in Excel.

<u>Risultati effettivi</u>:

Il rapporto ordine cliente CSV non mostra correttamente i caratteri speciali.


## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
