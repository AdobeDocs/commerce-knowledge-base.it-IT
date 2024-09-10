---
title: "ACSD-57045: le riscritture URL causano un ciclo di pagina infinito dopo che [!UICONTROL Website Root] è stato deselezionato da [!UICONTROL Hierarchy]"
description: Applicare la patch ACSD-57045 per risolvere il problema di Adobe Commerce, per cui le riscritture URL causano un ciclo di pagine infinito dopo la deselezione di [!UICONTROL Website Root] da [!UICONTROL Hierarchy].
feature: CMS
role: Admin, Developer
source-git-commit: df6cfc392f6afa4639a1ab9da52a85b8b15878d2
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 0%

---


# ACSD-57045: le riscritture URL causano un ciclo di pagine infinito dopo la deselezione di [!UICONTROL Website Root] da [!UICONTROL Hierarchy]

La patch ACSD-57045 risolve il problema per cui le riscritture URL causano un ciclo di pagine infinito dopo la deselezione di **[!UICONTROL Website Root]** da **[!UICONTROL Hierarchy]**. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49. L’ID della patch è ACSD-57045. Il problema è pianificato per essere risolto in Adobe Commerce 2.5.0.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.6-p7

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le riscritture URL causano un ciclo di pagine infinito dopo la rimozione di **[!UICONTROL Website Root]** da **[!UICONTROL Hierarchy]**.

<u>Passaggi da riprodurre</u>:

1. Crea una pagina CMS denominata *Test-Parent*.
1. Crea una pagina denominata *Test-Child* e nella sezione **[!UICONTROL Hierarchy]** seleziona **[!UICONTROL Website Root]** > **[!UICONTROL Parent]** e salva.
1. Vai a **[!UICONTROL Marketing]** > **[!UICONTROL URL Rewrites]**.
1. Si noti che sono disponibili due nuove riscritture:
   * Percorso della richiesta a *Test-Parent* che punta a *cms/page/view/page_id/ID_NUMBER_FOR_PAGE*
   * Percorso della richiesta a *Test-Child* che punta a *cms/page/view/page_id/ID_NUMBER_FOR_PAGE*
1. Visita la vetrina e aggiungi *test-child* all&#39;URL. Dovresti visualizzare la pagina figlia.
1. Effettua la stessa operazione, ma aggiungi *test-parent/test-child/* all&#39;URL e visualizza la stessa pagina.
1. Vai a **[!UICONTROL Marketing]** > **[!UICONTROL URL Rewrites]** e seleziona **[!UICONTROL Add URL Rewrite]**. Scegliere le impostazioni seguenti:
   * Tipo: *Personalizzato*
   * Percorso richiesta: *test-parent/test-child*
   * Percorso di destinazione: *test-child*
   * Tipo di reindirizzamento: *Permanente (301)*
1. Visita il percorso *test-parent/test-child* e dovresti essere reindirizzato a *test-child*.
1. Modificare la pagina figlio (**[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** > Scegli figlio e seleziona **[!UICONTROL Edit]**).
1. Nella sezione **[!UICONTROL Hierarchy]**, mantieni selezionato *Test-Parent*, ma deseleziona **[!UICONTROL Website Root]** e salva.
1. Vai a **[!UICONTROL Marketing]** > **[!UICONTROL URL Rewrites]** e osserva che il reindirizzamento originale *test-child* a *cms/page/view/page_id* è mancante e a quel punto è sostituito da un percorso che punta *test-child* a *test-parent/test-child*.
1. Visita la vetrina e prova a visitare la pagina *Test-Child*.

<u>Risultati previsti</u>:

La pagina *Test-Child* è aperta.

<u>Risultati effettivi</u>:

La pagina *Test-Child* non è aperta. Il browser tenta di aprire la pagina *test-parent/test-child* in un ciclo infinito.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
