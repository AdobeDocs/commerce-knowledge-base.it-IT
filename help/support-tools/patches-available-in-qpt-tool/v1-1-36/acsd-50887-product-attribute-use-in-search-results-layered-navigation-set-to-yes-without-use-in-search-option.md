---
title: '"ACSD-50887: *[!UICONTROL Use in Search Results Layered Navigation]* impostato su Sì senza *[!UICONTROL Use in Search]* opzione'''
description: Applica la patch ACSD-50887 per risolvere il problema Adobe Commerce relativo alla proprietà dell’attributo del prodotto*[!UICONTROL Use in Search Results Layered Navigation]* può essere impostato su *Yes* senza il simbolo *[!UICONTROL Use in Search]* l'opzione è impostata anche su *Yes*.
feature: Attributes, Products, Search, Storefront
role: Admin, Developer
exl-id: b597709b-7489-41a0-b1ff-d68d0def0b46
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# ACSD-50887 *[!UICONTROL Use in Search Results Layered Navigation]* imposta su *Sì* senza *[!UICONTROL Use in Search]* opzione

La patch ACSD-50887 risolve il problema relativo alla proprietà dell’attributo del prodotto *[!UICONTROL Use in Search Results Layered Navigation]* può essere impostato su *Sì* senza *[!UICONTROL Use in Search]* opzione impostata anche su *Sì*. Questa patch è disponibile quando [!DNL Quality Patches Tool (QPT)] 1.1.36. L’ID della patch è ACSD-50887. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Proprietà attributo prodotto *[!UICONTROL Use in Search Results Layered Navigation]* può essere impostato su *Sì* senza *[!UICONTROL Use in Search]* opzione impostata anche su *Sì*.

Queste impostazioni sono state progettate per essere utilizzate insieme. Con il cerotto applicato, quando *[!UICONTROL Use in Search]* è impostata su *No*, il *[!UICONTROL Use in Search Results Layered Navigation]* l&#39;opzione è nascosta per funzionare come se fosse impostata anche su *No*.

<u>Passaggi da riprodurre</u>:

1. In Admin, passa a **[!UICONTROL Stores]** > **[!UICONTROL Attribute]** > **[!UICONTROL Product]** e creare un attributo con il tipo multiselect e impostare quanto segue:

   * *[!UICONTROL Use in Search]= No*
   * *[!UICONTROL Use in Layered Navigation]= (Qualsiasi opzione)*
   * *[!UICONTROL Use in Search Results Layered Navigation]= Sì*
   * *Nome = Test_attribute*
   * *Opzioni*:
      * *Adesivo*
      * *Selettore*

1. Aggiungere il nuovo attributo al set di attributi predefinito.
1. Crea due prodotti:

   1. Primo prodotto:
      * Nome = Sticker
      * Imposta prezzo, QTÀ, Peso su 1
      * Test_attribute = opzione di selezione *Adesivo*

   1. Secondo prodotto:
      * Nome = Selettore
      * Imposta prezzo, QTÀ, Peso su 1
      * Test_attribute = seleziona entrambe le opzioni

1. Esegui `catalogsearch_fulltext` reindicizza:

   `bin/magento indexer:reindex catalogsearch_fulltext`

1. Ricerca per parola *adesivo* sul vetrina.

<u>Risultati previsti</u>:

Solo il prodotto *Adesivo* viene restituito, perché [!DNL Elasticsearch] non indicizza Test_attribute quando *[!UICONTROL Use in Search]* è stato impostato su *No*.

<u>Risultati effettivi</u>:

Entrambi i prodotti vengono restituiti.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
