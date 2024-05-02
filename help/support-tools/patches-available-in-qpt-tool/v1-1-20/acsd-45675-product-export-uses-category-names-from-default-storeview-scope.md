---
title: "ACSD-45675: l’esportazione del prodotto utilizza nomi di categoria dall’ambito di visualizzazione predefinito dell’archivio"
description: La patch ACSD-45675 risolve il problema relativo all’esportazione di prodotti che utilizza nomi di categoria dell’ambito predefinito di visualizzazione archivio. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20. L’ID della patch è ACSD-45675. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.
exl-id: 9edd718e-4c0c-44dd-b802-07c9ec7c182a
feature: Categories, Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-45675: l’esportazione del prodotto utilizza i nomi delle categorie dall’ambito di visualizzazione predefinito dell’archivio

La patch ACSD-45675 risolve il problema relativo all’esportazione di prodotti che utilizza nomi di categoria dell’ambito predefinito di visualizzazione archivio. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20. L’ID della patch è ACSD-45675. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’esportazione del prodotto utilizza i nomi delle categorie dell’ambito di visualizzazione predefinito dell’archivio.

<u>Passaggi da riprodurre</u>:

1. Creare una visualizzazione personalizzata dello store **[!UICONTROL Thai]** all&#39;interno del negozio principale.
1. Marca **[!UICONTROL Thai]** la visualizzazione store predefinita del sito web principale.
1. Crea la seguente struttura di categorie in **[!UICONTROL Default Category]**:

   *[!UICONTROL Default category/Tea/Black]*

1. Seleziona la categoria **[!UICONTROL Tea]** e modificare la **[!UICONTROL Scope]** a **[!UICONTROL Thai]**.
1. Imposta il **[!UICONTROL Category Name]** as **[!UICONTROL ชาดำ]**.
1. Creare un prodotto semplice **[!UICONTROL SP001]** e assegna la categoria **[!UICONTROL Black]**.
1. Assicurarsi che il cron non venga eseguito.
1. Esportare un prodotto. Filtra per SKU e seleziona **[!UICONTROL SP001]**.
1. Controlla la **[!UICONTROL categories]** nel file CSV esportato.

<u>Risultati previsti</u>:

Poiché non è stato selezionato alcun archivio durante l’esportazione, dovresti ottenere un percorso di categoria simile al seguente: *[!UICONTROL Default Category/Tea/Black]*.

<u>Risultati effettivi</u>:

Il percorso della categoria ha lingue diverse: *[!UICONTROL Default Category/ชาดำ/Black]*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tools] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida allo strumento Patch di qualità.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in [!DNL QPT], fare riferimento a [Patch disponibili in [!DNL QPT]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida allo strumento Patch di qualità.
