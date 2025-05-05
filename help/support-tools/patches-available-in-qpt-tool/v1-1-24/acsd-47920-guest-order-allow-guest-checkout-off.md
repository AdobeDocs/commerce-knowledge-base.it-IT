---
title: 'ACSD-47920: un utente guest può effettuare ordini tramite API REST anche quando [!UICONTROL Allow Guest Checkout] è disattivato'
description: Applicare la patch ACSD-47920 per risolvere il problema di Adobe Commerce, in cui è possibile effettuare ordini tramite API REST come utente guest anche quando [!UICONTROL Allow Guest Checkout] è disattivato.
exl-id: 8726eac4-ab19-4232-8e15-270d09bdc0a5
feature: REST, Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# ACSD-47920: un utente guest può effettuare ordini tramite API REST anche quando **[!UICONTROL Allow Guest Checkout]** è disattivato

La patch ACSD-47920 risolve il problema che consente di effettuare ordini tramite API REST come utente guest anche quando **[!UICONTROL Allow Guest Checkout]** è disattivato. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24. L’ID della patch è ACSD-47920. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli ordini possono essere inseriti tramite API REST come utente guest anche quando **[!UICONTROL Allow Guest Checkout]** è disattivato.

<u>Passaggi da riprodurre</u>:

1. Vai a Amministrazione Adobe Commerce > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]** > e imposta **[!UICONTROL Allow Guest Checkout]** su _No_.
1. Utilizza l’API REST per aggiungere un prodotto al carrello e effettuare un ordine.

<u>Risultati previsti</u>:

L&#39;API di estrazione guest restituisce un errore *[!UICONTROL Sorry, guest checkout is not available]* se **[!UICONTROL Allow Guest Checkout]** è impostato su _No_.

<u>Risultati effettivi</u>:

L&#39;API di estrazione guest consente di eseguire un ordine anche se **[!UICONTROL Allow Guest Checkout]** è impostato su _No_.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
