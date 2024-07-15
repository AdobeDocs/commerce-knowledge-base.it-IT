---
title: 'ACSD-48634: [!DNL JS] errori quando [!DNL Google Analytics Content Experiments] abilitato'
description: Applica la patch ACSD-48634 per correggere [!DNL JS] errori in una  [!DNL staging] pagina di aggiornamento quando [!DNL Google Analytics Content Experiments] è abilitato.
exl-id: 4a9f201d-eaf0-4e43-a1a1-0a9ffb0a2ead
feature: Catalog Management, Categories, Console, Page Content
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-48634: [!DNL JS] errori quando [!DNL Google Analytics Content Experiments] è abilitato

La patch ACSD-48634 corregge [!DNL JS] errori in una pagina di aggiornamento [!DNL staging] quando [!DNL Google Analytics Content Experiments] è abilitato. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27. L’ID della patch è ACSD-48634. Il problema è stato risolto in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

[!DNL JS] errori si verificano in una pagina di aggiornamento [!DNL staging] quando [!DNL Google Analytics Content Experiments] è abilitato.

<u>Passaggi da riprodurre</u>:

1. In **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**, creare un altro sito Web, store e **[!UICONTROL Store View]**. Assicurarsi che **[!UICONTROL Store View]** sia *[!UICONTROL Enabled]*.
1. Configura **[!DNL Configure Google Analytics]** andando in **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Google API]**:
   * Per **[!DNL Main]** e altri siti Web [!DNL scope]:
      * **[!UICONTROL Enabled]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Account type]**: *[!UICONTROL Google Tag Manager]*
      * **[!UICONTROL Anonymize IP]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Enable Content Experiments]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Container Id]**: *[!UICONTROL (GTM container ID)]*
      * **[!DNL Uncheck]** *[!UICONTROL Use Default]* per altri campi, ma non modificarli.
   * Per **[!DNL Default Config]** [!DNL scope]:
      * **[!UICONTROL Enabled]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Account type]**: *[!UICONTROL Universal Analytics]*
      * **[!UICONTROL Account Number]**: *[!UICONTROL (Universal Analytics account number)]*
      * **[!UICONTROL Anonymize IP]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Enable Content Experiments]**: *[!UICONTROL Yes]*
1. Disabilitare **[!DNL Configure Google Analytics]** su **[!DNL Default Config]** [!DNL scope] modificando **[!UICONTROL Enable]** da *[!UICONTROL Yes]* a *[!UICONTROL No]*. Assicurati di non cambiare altro!
1. Vai a **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**.
1. Crea e modifica qualsiasi **[!UICONTROL category]** e aggiungi un aggiornamento pianificato:
   * Qualsiasi nome, data di inizio futura, data di fine futura ed eventuali modifiche in **[!UICONTROL category]** ([!UICONTROL For Example]: *[!UICONTROL disable category]*).
1. Salvare l&#39;aggiornamento e verificare la presenza di errori in [!DNL browser developer console].

<u>Risultati previsti</u>:

Nessun errore [!DNL JS] e le modifiche all&#39;aggiornamento [!DNL staging] sono state salvate correttamente.

<u>Risultati effettivi</u>:

[!DNL JS] errori sono visibili nella console, il modulo non è corretto e [!DNL spinner] non viene mai disabilitato dopo il salvataggio.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
