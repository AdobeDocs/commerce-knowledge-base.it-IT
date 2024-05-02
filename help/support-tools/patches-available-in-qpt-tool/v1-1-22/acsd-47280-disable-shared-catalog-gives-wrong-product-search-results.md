---
title: '''[!DNL ACSD-47280]: la disattivazione del catalogo condiviso genera risultati di ricerca del prodotto errati"'
description: Applica [!DNL ACSD-47280] patch per correggere la visualizzazione dei risultati di ricerca corretti quando la funzione di catalogo condiviso è disabilitata.
exl-id: 98bbae42-fd68-4b54-823d-189d742cc35f
source-git-commit: 975f5b5c95ad488128a5dbb3488b8d54f7b73b59
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# [!DNL ACSD-47280]: la disattivazione del catalogo condiviso genera risultati di ricerca errati

Il [!DNL ACSD-47280] patch corregge la visualizzazione dei risultati di ricerca corretti quando [!DNL shared catalog] funzionalità disabilitata. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.22. Il [!DNL patch ID] è [!DNL ACSD-47280]. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.5

**Compatibile con le versioni di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza il [!DNL patch ID] come parola chiave di ricerca per individuare la patch.

## Problema

Disattivazione [!DNL shared catalog] fornisce risultati di ricerca del prodotto errati.

<u>Prerequisiti</u>:

* [!DNL B2B] moduli installati

<u>Passaggi da riprodurre</u>:

1. Creare un secondo sito Web.
1. Assegna un prodotto al secondo sito Web.
1. Controlla i prodotti sulla **secondo sito web** utilizzo [!DNL GraphQL]:

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

1. Abilita **[!UICONTROL Shared Catalog]** su impostazione predefinita [!DNL scope].
1. Il [!DNL GraphQL] La richiesta non mostra più alcun prodotto per il secondo sito web, che è il risultato corretto.
1. Vai a [!DNL scope] del secondo sito Web e disabilita **[!UICONTROL Company]**.

<u>Risultati previsti</u>:

Il [!DNL GraphQL] La richiesta deve comunque mostrare i prodotti per il secondo sito web.

<u>Risultati effettivi</u>:

Il [!DNL GraphQL] La richiesta non mostra alcun prodotto per il secondo sito web.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
