---
title: "ACSD-49748: impossibile inviare gli inviti e-mail"
description: Applica la patch ACSD-49748 per risolvere il problema di Adobe Commerce che impedisce agli utenti di inviare inviti e-mail.
exl-id: 65de8ea9-e65c-463b-8cba-d35767d4343d
feature: Admin Workspace, Communications, Marketing Tools
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---

# ACSD-49748: impossibile inviare gli inviti e-mail

La patch ACSD-49748 risolve il problema che impediva agli utenti di inviare inviti e-mail. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29. L’ID della patch è ACSD-49748. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’errore *Si è verificato un errore durante l&#39;invio degli inviti* viene visualizzato quando si inviano gli inviti.

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL Admin Panel]** > **[!UICONTROL Marketing]** > **[!UICONTROL Private Sales]** > **[!UICONTROL Invitations]**.
1. Crea un invito e salvalo.
1. Vai a **[!UICONTROL Invitation Grid]** e seleziona un invito.
1. Invia l&#39;invito.

<u>Risultati previsti</u>:

Viene inviato un invito quando si fa clic su *[!UICONTROL Send Invitation]*.

<u>Risultati effettivi</u>:

L’errore *Si è verificato un errore durante l&#39;invio degli inviti* e l&#39;invito non viene inviato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.
