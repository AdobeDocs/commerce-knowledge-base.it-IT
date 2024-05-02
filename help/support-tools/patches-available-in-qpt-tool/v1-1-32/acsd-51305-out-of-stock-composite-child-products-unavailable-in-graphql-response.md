---
title: "ACSD-51305: prodotti secondari compositi esauriti non disponibili nella risposta GraphQL"
description: Applica la patch ACSD-51305 per risolvere il problema di Adobe Commerce per cui i prodotti secondari compositi esauriti non sono disponibili nella risposta di GraphQL.
exl-id: 0f33eb62-dfd3-4d07-b095-9ee6e9983c4d
feature: Categories, GraphQL, Orders, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# ACSD-51305: prodotti secondari compositi esauriti non disponibili nella risposta GraphQL

La patch ACSD-51305 risolve il problema se i prodotti secondari compositi esauriti non sono disponibili nella risposta di GraphQL. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.32. L’ID della patch è ACSD-51305. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I prodotti secondari compositi esauriti non sono disponibili nella risposta di GraphQL.

<u>Passaggi da riprodurre</u>:

1. Accedi al sito web dell’amministratore.
1. Crea una categoria (cat1, id=3).
1. Creare un *simple1* prodotto (esaurito, non visibile singolarmente, assegnato a *cat1*).
1. Creare un *simple2* prodotto (in magazzino, non visibile singolarmente, assegnato a *cat1*).
1. Creare un *bundle1* prodotto con *simple1* e *simple2* prodotti secondari come pulsante di scelta *option1* e assegnarli al *cat1* categoria.
1. Vai a **[!UICONTROL Admin]** > **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]**.

   * Imposta **[!UICONTROL Display Out of Stock Products]** a *Sì*.

1. Apri *bundle1* sul punto vendita e garantire che entrambi *simple1* e *simple2* i prodotti secondari sono visualizzati al suo interno.
1. Esegui la seguente query GraphQL:

   ```GraphQL
   {
       categoryList(filters: { ids: { in: ["3"] } }) {
           id
           name
           products(pageSize: 8, sort: { position: ASC }) {
               total_count
               items {
                   id
                   sku
                   name
                   ... on BundleProduct {
                       url_key
                       items {
                           title
                           sku
                           options {
                               quantity
                               position
                               is_default
                               product {
                                   id
                                   name
                                   sku
                               }
                           }
                       }
                   }
               }
           }
       }
   }
   ```

<u>Risultati previsti</u>:

Il **[!UICONTROL Product]** all&#39;interno della sezione **[!UICONTROL Options]** il blocco non è vuoto.

<u>Risultati effettivi</u>:

Il **[!UICONTROL Product]** all&#39;interno della sezione **[!UICONTROL Options]** blocco vuoto.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
