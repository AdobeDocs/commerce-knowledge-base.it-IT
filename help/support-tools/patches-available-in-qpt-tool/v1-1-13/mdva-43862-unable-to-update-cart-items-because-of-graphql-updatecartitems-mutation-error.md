---
title: "MDVA-43862: il cliente non può aggiornare gli elementi del carrello a causa di un errore di mutazione di GraphQL UpdateCartItems"
description: La patch MDVA-43862 risolve il problema che impedisce al cliente di aggiornare gli elementi del carrello a causa di un errore di mutazione di GraphQL UpdateCartItems. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13. L'ID della patch è MDVA-43862. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
exl-id: 5f0a2970-34a8-4a25-baf8-15c007f97084
feature: GraphQL, Orders, Shopping Cart
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# MDVA-43862: impossibile aggiornare gli elementi del carrello a causa di un errore di mutazione di GraphQL UpdateCartItems

La patch MDVA-43862 risolve il problema che impedisce al cliente di aggiornare gli elementi del carrello a causa di un errore di mutazione di GraphQL UpdateCartItems. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13. L&#39;ID della patch è MDVA-43862. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1, 2.4.2-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.3 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il cliente non può aggiornare gli articoli del carrello a causa di un errore di mutazione di GraphQL UpdateCartItems.

<u>Passaggi da riprodurre</u>:

1. Creare un prodotto configurabile (MH01) assegnando un semplice (MH01-XL-Gray).
1. Vai a Amministrazione Commerce > **Catalogo** > **Prodotti** > **SKU** > **MH01** > **Opzioni personalizzabili**.
1. Aggiungi un’opzione personalizzata al prodotto.
   * Titolo opzione: Opzione1
   * Tipo di opzione: Campo
   * Obbligatorio: sì
   * Prezzo: 10.00
   * Tipo di prezzo: fisso
   * SKU: MHC1
   * Numero massimo di caratteri: 25
1. Esegui la query GraphQL seguente per generare l’ID carrello.

   ```GraphQL
   mutation {
     createEmptyCart
   }
   ```

1. Prendi nota del codice ID del carrello.
1. Esegui la query seguente per aggiungere al carrello un prodotto configurabile:

   ```GraphQL
   mutation {
   addConfigurableProductsToCart(
   input: {
       cart_id: "<cart ID from above step>",
       cart_items: [{
       parent_sku: "MH01",
       data: {
           quantity: 1,
           sku: "MH01-XL-Gray"
           },
           customizable_options: {
               id: 1,
               value_string: "2"
               }
           }
       ]
   }
   )
   {
   cart {
     items {
       uid
       quantity
       product {
         name
         sku
       }
       ... on ConfigurableCartItem {
         configurable_options {
           option_label
         }
       }
     }
   }
   }
   }
   ```

1. Noterai che il carrello è compilato con l’articolo configurabile.
1. Prendi nota dell’UID restituito.
1. Esegui nuovamente la query seguente per aggiornare l’elemento del carrello.

   ```GraphQL
   mutation {
     updateCartItems(
       input: {
         cart_id: "<cart ID from previous step>",
         cart_items: [
           {
             cart_item_uid: "<uid from previous step>"
             quantity: 3,
             customizable_options:[{
                 id: 1,
                 value_string: "67"
             }]
           }
         ]
       }
     ){
       cart {
         items {
           uid
           product {
             name
           }
           quantity
         }
         prices {
           grand_total{
             value
             currency
           }
         }
       }
     }
   }
   ```

1. Osserva la risposta.

<u>Risultati previsti</u>:

Il carrello viene aggiornato senza alcun problema.

<u>Risultati effettivi</u>:

Viene visualizzato il seguente errore:

```GraphQL
{
  "errors": [
    {
      "message": "Could not update cart item: You need to choose options for your item.",
      "extensions": {
        "category": "graphql-input"
      },
      "locations": [
        {
          "line": 2,
          "column": 3
        }
      ],
      "path": [
        "updateCartItems"
      ]
    }
  ],
  "data": {
    "updateCartItems": null
  }
}
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella documentazione per gli sviluppatori.
