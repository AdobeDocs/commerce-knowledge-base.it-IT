---
title: '"ACSD-56515: l’amministratore con autorizzazioni a livello di sito web non può modificare [!UICONTROL Dynamic Block]'''
description: Applica la patch ACSD-56515 per risolvere il problema di Adobe Commerce, in cui l’amministratore con autorizzazioni a livello di sito web non può aggiungere o modificare il [!UICONTROL Dynamic Block].
feature: Roles/Permissions, Admin Workspace
role: Admin, Developer
exl-id: 5aa6b11e-b467-4076-ad36-162966cbf6df
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-56515: l’amministratore con autorizzazioni a livello di sito web non può modificare [!UICONTROL Dynamic Block]

La patch ACSD-56515 risolve il problema per cui l’amministratore con autorizzazioni a livello di sito web non può aggiungere o modificare il [!UICONTROL Dynamic Block]. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45. L’ID della patch è ACSD-56515. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’amministratore con autorizzazioni a livello di sito web non può aggiungere o modificare il [!UICONTROL Dynamic Block].

<u>Passaggi da riprodurre</u>:

1. Crea un sito Web secondario con store e storeview.
1. Vai a **[!UICONTROL System]** > **[!UICONTROL Permissions]** > **[!UICONTROL User Roles]** e creare un ruolo utente limitato all’ambito del sito web secondario con tutte le risorse disponibili.
1. Crea un utente amministratore con il ruolo creato in precedenza.
1. Accedi con l&#39;utente amministratore con restrizioni e crea un [!UICONTROL Dynamic Block].

<u>Risultati previsti</u>:

L’utente amministratore con restrizioni al sito web può creare una [!UICONTROL Dynamic Block].

<u>Risultati effettivi</u>:

Viene visualizzato il seguente errore: *Sono necessarie altre autorizzazioni per visualizzare questo elemento*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
