---
title: '"ACSD-48634: [!DNL JS] errori quando [!DNL Google Analytics Content Experiments] abilitato'''
description: Applicare la patch ACSD-48634 per correggere [!DNL JS] errori in un [!DNL staging] aggiorna pagina quando [!DNL Google Analytics Content Experiments] è abilitato.
exl-id: 4a9f201d-eaf0-4e43-a1a1-0a9ffb0a2ead
feature: Catalog Management, Categories, Console, Page Content
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-48634 [!DNL JS] errori quando [!DNL Google Analytics Content Experiments] abilitato

Correzioni della patch ACSD-48634 [!DNL JS] errori in un [!DNL staging] aggiorna pagina quando [!DNL Google Analytics Content Experiments] è abilitato. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27. L’ID della patch è ACSD-48634. Il problema è stato risolto in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

[!DNL JS] si verificano errori in un [!DNL staging] aggiorna pagina quando [!DNL Google Analytics Content Experiments] è abilitato.

<u>Passaggi da riprodurre</u>:

1. In entrata **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**, creare un sito Web, uno store e **[!UICONTROL Store View]**. Assicurati che le **[!UICONTROL Store View]** è *[!UICONTROL Enabled]*.
1. Configura **[!DNL Configure Google Analytics]** andando in **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Google API]**:
   * Per **[!DNL Main]** e siti web aggiuntivi [!DNL scope]:
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
1. Disattiva **[!DNL Configure Google Analytics]** il **[!DNL Default Config]** [!DNL scope] modificando **[!UICONTROL Enable]** da *[!UICONTROL Yes]* a *[!UICONTROL No]*. Assicurati di non cambiare altro!
1. Vai a **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**.
1. Crea e modifica qualsiasi **[!UICONTROL category]** e aggiungi un aggiornamento pianificato:
   * Qualsiasi nome, data di inizio futura, data di fine futura ed eventuali modifiche in **[!UICONTROL category]** ([!UICONTROL For Example]: *[!UICONTROL disable category]*).
1. Salva l’aggiornamento e controlla [!DNL browser developer console] per gli errori.

<u>Risultati previsti</u>:

No [!DNL JS] e le modifiche apportate al [!DNL staging] l&#39;aggiornamento è stato salvato.

<u>Risultati effettivi</u>:

[!DNL JS] Gli errori sono visibili nella console, il modulo non è formattato correttamente e il [!DNL spinner] non viene mai disattivato dopo il salvataggio.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
