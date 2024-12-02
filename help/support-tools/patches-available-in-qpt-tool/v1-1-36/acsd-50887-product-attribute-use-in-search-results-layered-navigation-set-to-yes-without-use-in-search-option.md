---
title: 'ACSD-50887: *[!UICONTROL Use in Search Results Layered Navigation]* impostato su Sì senza l''opzione *[!UICONTROL Use in Search]*'
description: Applicare la patch ACSD-50887 per risolvere il problema di Adobe Commerce per cui la proprietà dell'attributo del prodotto *[!UICONTROL Use in Search Results Layered Navigation]* può essere impostata su *Yes* senza che anche l'opzione *[!UICONTROL Use in Search]* sia impostata su *Yes*.
feature: Attributes, Products, Search, Storefront
role: Admin, Developer
exl-id: b597709b-7489-41a0-b1ff-d68d0def0b46
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# ACSD-50887: *[!UICONTROL Use in Search Results Layered Navigation]* impostato su *Sì* senza l&#39;opzione *[!UICONTROL Use in Search]*

La patch ACSD-50887 risolve il problema per cui la proprietà dell&#39;attributo di prodotto *[!UICONTROL Use in Search Results Layered Navigation]* può essere impostata su *Sì* senza che anche l&#39;opzione *[!UICONTROL Use in Search]* sia impostata su *Sì*. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.36. L’ID della patch è ACSD-50887. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

È possibile impostare la proprietà dell&#39;attributo di prodotto *[!UICONTROL Use in Search Results Layered Navigation]* su *Yes* senza impostare anche l&#39;opzione *[!UICONTROL Use in Search]* su *Yes*.

Queste impostazioni sono state progettate per essere utilizzate insieme. Con la patch applicata, quando l&#39;opzione *[!UICONTROL Use in Search]* è impostata su *No*, l&#39;opzione *[!UICONTROL Use in Search Results Layered Navigation]* è nascosta e funziona come se fosse impostata anche su *No*.

<u>Passaggi da riprodurre</u>:

1. In Amministrazione, passare a **[!UICONTROL Stores]** > **[!UICONTROL Attribute]** > **[!UICONTROL Product]** e creare un attributo con il tipo a selezione multipla e impostare quanto segue:

   * *[!UICONTROL Use in Search]= No*
   * *[!UICONTROL Use in Layered Navigation]= (Qualsiasi opzione)*
   * *[!UICONTROL Use in Search Results Layered Navigation]= Sì*
   * *Nome = Test_attribute*
   * *Opzioni*:
      * *Sticker*
      * *Selettore*

1. Aggiungere il nuovo attributo al set di attributi predefinito.
1. Crea due prodotti:

   1. Primo prodotto:
      * Nome = Sticker
      * Imposta prezzo, QTÀ, Peso su 1
      * Test_attribute = opzione di selezione *Sticker*

   1. Secondo prodotto:
      * Nome = Selettore
      * Imposta prezzo, QTÀ, Peso su 1
      * Test_attribute = seleziona entrambe le opzioni

1. Esegui reindicizzazione `catalogsearch_fulltext`:

   `bin/magento indexer:reindex catalogsearch_fulltext`

1. Effettua la ricerca in base alla parola *sticker* nella vetrina.

<u>Risultati previsti</u>:

Viene restituito solo il prodotto *Sticker*, perché [!DNL Elasticsearch] non indicizza Test_attribute quando *[!UICONTROL Use in Search]* è stato impostato su *No*.

<u>Risultati effettivi</u>:

Entrambi i prodotti vengono restituiti.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
