---
title: 'ACSD-45817: la mutazione dei prodotti GraphQL offre tutte le varianti configurabili'
description: La patch ACSD-45817 risolve il problema in cui una mutazione "products" di GraphQL per un archivio specifico restituisce tutte le varianti configurabili, comprese quelle non assegnate all’archivio richiesto. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18. L’ID della patch è ACSD-45817. Il problema è stato risolto in Adobe Commerce 2.4.4.
exl-id: 3d61d1aa-36b5-471d-929b-7df8ce65c791
feature: GraphQL, Configuration, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# ACSD-45817: la mutazione dei prodotti GraphQL offre tutte le varianti configurabili

La patch ACSD-45817 risolve il problema per cui una mutazione di GraphQL `products` per un archivio specifico restituisce tutte le varianti configurabili, incluse quelle non assegnate all&#39;archivio richiesto. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18. L’ID della patch è ACSD-45817. Il problema è stato risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.3-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Una mutazione di GraphQL `products` per un archivio specifico restituisce tutte le varianti configurabili, incluse quelle non assegnate all&#39;archivio richiesto.

<u>Prerequisiti</u>:

Creare un secondo sito Web, un secondo store e una seconda visualizzazione store.

<u>Passaggi da riprodurre</u>:

1. Creare un prodotto configurabile con due sottoprodotti: &quot;configurable-a&quot; e &quot;configurable-b&quot;.
1. Assegna il prodotto configurabile a entrambi i siti web.
1. Assegna una sola variante &quot;configurabile-a&quot; al secondo sito web.
1. Vai a **Storefront**, passa al secondo sito Web e apri il prodotto configurabile.
1. Assicurati di visualizzare solo un’opzione figlio: &quot;configurable-a&quot;.
1. Esegui una query GraphQL utilizzando l&#39;endpoint `POST: /graphql` e `Headers: "store" = "new"`

   ```GraphQL
   {
     products(filter: { sku: { eq: "configurable" } }) {
       items {
         id
         attribute_set_id
         name
         sku
         __typename
         price_range{
           minimum_price{
             regular_price{
               value
               currency
             }
           }
         }
         categories {
           id
         }
         ... on ConfigurableProduct {
           configurable_options {
             id
             attribute_id_v2
             label
             position
             use_default
             attribute_code
             values {
               value_index
               label
             }
             product_id
           }
           variants {
             product {
               id
               name
               sku
               attribute_set_id
               ... on PhysicalProductInterface {
                 weight
               }
               price_range{
                 minimum_price{
                   regular_price{
                     value
                     currency
                   }
                 }
               }
             }
             attributes {
               uid
               label
               code
               value_index
             }
           }
         }
       }
     }
   }
   ```

<u>Risultati previsti</u>:

La variante &quot;configurable-b&quot; non è assegnata al secondo sito web e non deve essere visualizzata nella risposta.

<u>Risultati effettivi</u>:

La variante &quot;configurable-b&quot; viene visualizzata nella risposta.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella documentazione per gli sviluppatori.
