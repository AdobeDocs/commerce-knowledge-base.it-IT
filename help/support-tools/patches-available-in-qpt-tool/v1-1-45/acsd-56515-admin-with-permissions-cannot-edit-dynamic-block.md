---
title: 'ACSD-56515: l''amministratore con autorizzazioni a livello di sito Web non può modificare [!UICONTROL Dynamic Block]'
description: Applicare la patch ACSD-56515 per risolvere il problema di Adobe Commerce che impedisce all'amministratore con autorizzazioni a livello di sito Web di aggiungere o modificare [!UICONTROL Dynamic Block].
feature: Roles/Permissions, Admin Workspace
role: Admin, Developer
exl-id: 5aa6b11e-b467-4076-ad36-162966cbf6df
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-56515: l&#39;amministratore con autorizzazioni a livello di sito Web non può modificare [!UICONTROL Dynamic Block]

La patch ACSD-56515 risolve il problema che impediva all&#39;amministratore con autorizzazioni a livello di sito Web di aggiungere o modificare [!UICONTROL Dynamic Block]. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45. L’ID della patch è ACSD-56515. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;amministratore con autorizzazioni a livello di sito Web non può aggiungere o modificare [!UICONTROL Dynamic Block].

<u>Passaggi da riprodurre</u>:

1. Crea un sito Web secondario con store e storeview.
1. Vai a **[!UICONTROL System]** > **[!UICONTROL Permissions]** > **[!UICONTROL User Roles]** e crea un ruolo utente limitato all&#39;ambito del sito Web secondario con tutte le risorse disponibili.
1. Crea un utente amministratore con il ruolo creato in precedenza.
1. Accedere con l&#39;utente amministratore con restrizioni e creare un [!UICONTROL Dynamic Block].

<u>Risultati previsti</u>:

L&#39;utente amministratore con restrizioni al sito Web può creare [!UICONTROL Dynamic Block].

<u>Risultati effettivi</u>:

Errore: *Per visualizzare l&#39;elemento sono necessarie altre autorizzazioni*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
