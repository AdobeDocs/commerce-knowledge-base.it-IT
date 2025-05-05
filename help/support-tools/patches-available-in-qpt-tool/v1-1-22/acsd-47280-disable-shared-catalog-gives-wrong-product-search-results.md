---
title: '[!DNL ACSD-47280]: la disabilitazione del catalogo condiviso fornisce risultati di ricerca del prodotto errati'
description: Applica la patch  [!DNL ACSD-47280]  per correggere la visualizzazione dei risultati di ricerca corretti quando la funzionalità di catalogo condiviso è disabilitata.
exl-id: 98bbae42-fd68-4b54-823d-189d742cc35f
source-git-commit: 975f5b5c95ad488128a5dbb3488b8d54f7b73b59
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# [!DNL ACSD-47280]: la disabilitazione del catalogo condiviso genera risultati di ricerca prodotti errati

La patch [!DNL ACSD-47280] corregge la visualizzazione dei risultati di ricerca corretti quando la funzionalità [!DNL shared catalog] è disabilitata. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.22. [!DNL patch ID] è [!DNL ACSD-47280]. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.5

**Compatibile con le versioni di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizzare [!DNL patch ID] come parola chiave di ricerca per individuare la patch.

## Problema

La disabilitazione di [!DNL shared catalog] genera risultati di ricerca prodotti errati.

<u>Prerequisiti</u>:

* [!DNL B2B] moduli installati

<u>Passaggi da riprodurre</u>:

1. Creare un secondo sito Web.
1. Assegna un prodotto al secondo sito Web.
1. Controlla i prodotti sul **secondo sito Web** utilizzando [!DNL GraphQL]:

   ```GraphQL
   {
     products(search: "bag", pageSize: 2) {
       total_count
       items {
         name
         sku
       }
       page_info {
         page_size
         current_page
       }
     }
   }
   ```

1. Abilita **[!UICONTROL Shared Catalog]** su [!DNL scope] predefinito.
1. La richiesta [!DNL GraphQL] non mostra più alcun prodotto per il secondo sito Web, che è il risultato corretto.
1. Andare al [!DNL scope] del secondo sito Web e disabilitare **[!UICONTROL Company]**.

<u>Risultati previsti</u>:

La richiesta [!DNL GraphQL] deve ancora mostrare i prodotti per il secondo sito Web.

<u>Risultati effettivi</u>:

La richiesta [!DNL GraphQL] non mostra alcun prodotto per il secondo sito Web.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
