---
title: '"ACSD-47336: [!UICONTROL Something went wrong] errore durante la rimozione delle notifiche in Adobe Commerce Admin'''
description: Applica la patch ACSD-47336 per risolvere il problema di Adobe Commerce che l’utente vede [!UICONTROL Something went wrong] errore durante la rimozione delle notifiche in [!DNL Commerce] Amministratore
exl-id: 7561f055-ce04-4a49-8c58-271c24420a60
feature: Admin Workspace
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-47336 _[!UICONTROL Something went wrong]_errore durante la rimozione delle notifiche in Adobe Commerce Admin

La patch ACSD-47336 risolve il problema in cui l’utente visualizza _[!UICONTROL Something went wrong]_errore durante la rimozione delle notifiche in [!DNL Commerce] Amministratore Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24. L’ID della patch è ACSD-47336. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione): 2.4.5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione): 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’utente vede _[!UICONTROL Something went wrong]_errore durante la rimozione delle notifiche in [!DNL Commerce] Amministratore

<u>Passaggi da riprodurre</u>:

1. Eseguire un’operazione in blocco (ad esempio, aggiornamento in blocco degli attributi del prodotto dalla griglia del prodotto).
1. Completa l’operazione (ad es. esegui `bin/magento queue:consumer:start product_action_attribute.update`).
1. Aggiorna il [!DNL Commerce] pagina Amministratore, espandi la sezione notifica amministratore e fai clic sul pulsante **[!UICONTROL Dismiss All Completed Tasks]** collegamento.

<u>Risultati previsti</u>:

Il _[!UICONTROL Something went wrong]_L&#39;errore non deve essere visualizzato quando si cancellano le attività completate.

<u>Risultati effettivi</u>:

Il _[!UICONTROL Something went wrong]_viene visualizzato un errore.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
