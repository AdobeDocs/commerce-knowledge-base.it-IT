---
title: '"ACSD-47920: un utente ospite può effettuare ordini tramite API REST anche quando [!UICONTROL Allow Guest Checkout] è disattivato'''
description: Applica la patch ACSD-47920 per risolvere il problema di Adobe Commerce, dove è possibile effettuare ordini tramite API REST come utente guest anche quando [!UICONTROL Allow Guest Checkout] è disattivato.
exl-id: 8726eac4-ab19-4232-8e15-270d09bdc0a5
feature: REST, Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# ACSD-47920: un utente ospite può effettuare ordini tramite API REST anche quando **[!UICONTROL Allow Guest Checkout]** è disattivato

La patch ACSD-47920 risolve il problema che consente di effettuare ordini tramite API REST come utente guest anche quando **[!UICONTROL Allow Guest Checkout]** è disattivato. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24. L’ID della patch è ACSD-47920. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli ordini possono essere inseriti tramite API REST come utente guest anche quando **[!UICONTROL Allow Guest Checkout]** è disattivato.

<u>Passaggi da riprodurre</u>:

1. Vai a Amministrazione di Adobe Commerce > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]** > e impostare **[!UICONTROL Allow Guest Checkout]** a _No_.
1. Utilizza l’API REST per aggiungere un prodotto al carrello e effettuare un ordine.

<u>Risultati previsti</u>:

L’API di estrazione guest restituisce un errore *[!UICONTROL Sorry, guest checkout is not available]* se **[!UICONTROL Allow Guest Checkout]** è impostato su _No_.

<u>Risultati effettivi</u>:

L’API di pagamento per gli ospiti consente di effettuare un ordine anche se **[!UICONTROL Allow Guest Checkout]** è impostato su _No_.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
