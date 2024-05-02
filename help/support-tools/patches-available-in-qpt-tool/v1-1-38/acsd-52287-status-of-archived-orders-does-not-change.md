---
title: "ACSD-52287: lo stato degli ordini archiviati non cambia"
description: Applicare la patch ACSD-52287 per risolvere il problema Adobe Commerce, in cui lo stato degli ordini archiviati non cambia da *completato* a *chiuso* sulla griglia dopo l'invio della nota di credito.
feature: Orders, Checkout
role: Admin, Developer
exl-id: c88c5c87-eec7-4105-9e4e-815d0888a34b
source-git-commit: 178023177975f210ebf7dd07e8c75cfe3ac89ff1
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# ACSD-52287: lo stato degli ordini archiviati non cambia

La patch ACSD-52287 risolve il problema che impedisce la modifica dello stato degli ordini archiviati da *completato* a *chiuso* sulla griglia dopo l&#39;invio della nota di accredito. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.38. L’ID della patch è ACSD-52287. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Lo stato degli ordini archiviati non cambia da *completato* a *chiuso* sulla griglia dopo l&#39;invio della nota di accredito.

<u>Passaggi da riprodurre</u>:

1. Configura *[!UICONTROL Asynchronous Indexing]*.
   * Nella barra laterale Amministratore, vai a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]**.
   * Nel pannello a sinistra, espandi **[!UICONTROL Advanced]** e scegliere **[!UICONTROL Developer]** sotto.
   * Espandi **[!UICONTROL Grid Settings]** sezione.
   * Imposta *[!UICONTROL Asynchronous indexing]* a *Sì*.
   * Clic **[!UICONTROL Save Config]**.
1. Configurare *[!UICONTROL Order Archive]*.
   * Nella barra laterale Amministratore, vai a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]**.
   * Nel pannello a sinistra, espandi **[!UICONTROL Sales]** e scegliere **[!UICONTROL Sales]** sotto.
   * Espandi **[!UICONTROL Orders, Invoices, Shipments, Credit Memos Archiving]** sezione.
   * Imposta *[!UICONTROL Enable Archiving]* a *Sì* (Lascia le altre configurazioni come predefinite).
   * Clic **[!UICONTROL Save Config]**.
1. Inserisci un ordine nel front-end.
1. Esegui il [!DNL cron]  affinché l&#39;ordine venga visualizzato nel *[!UICONTROL Admin Order Grid]*.
1. Fatturare e spedire l&#39;ordine per aggiornare lo stato dell&#39;ordine in *Completa*.
1. Esegui il [!DNL cron]  per aggiornare *[!UICONTROL Sales Order Grid]* con lo stato dell’ordine più recente.
1. Archivia l’ordine.
1. Vai a *[!UICONTROL Archived order grid]*.
1. Aprire l&#39;ordine archiviato e rimborsare l&#39;ordine offline creando un [!UICONTROL Credit Memo] per rendere [!UICONTROL Order status]: *Chiuso*.
1. Esegui il [!DNL cron] per qualche volta.
1. Controlla la *[!UICONTROL Archived order grid]* per lo stato del nuovo ordine.

<u>Risultati previsti</u>:

L’ordine viene visualizzato come *Chiuso*.

<u>Risultati effettivi</u>:

L’ordine viene visualizzato come *Completa*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
