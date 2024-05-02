---
title: "ACSD-49574: impossibile aggiornare il prodotto gift card nel carrello tramite GraphQL"
description: Applica la patch ACSD-49574 per risolvere il problema di Adobe Commerce che impedisce l’aggiornamento di un prodotto gift card nel carrello tramite GraphQL.
exl-id: e446128f-c991-4c3c-8d1c-bbff6230e448
feature: Admin Workspace, Gift, GraphQL, Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACSD-49574: impossibile aggiornare il prodotto gift card nel carrello tramite GraphQL

La patch ACSD-49574 risolve il problema che impedisce l&#39;aggiornamento di un prodotto gift card nel carrello tramite GraphQL. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28. L’ID della patch è ACSD-49574. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Un prodotto gift card non può essere aggiornato nel carrello tramite GraphQL.

<u>Passaggi da riprodurre</u>:

1. Creare un prodotto gift card.
1. Aggiungi il prodotto gift card al carrello tramite GraphQL.
1. Prova ad aggiornare i campi dei prodotti gift card nel carrello tramite GraphQL utilizzando `updateCartItems` mutazione.

   Esempio di utilizzo di GraphQL:

   ```GraphQL
   mutation ($cartId: String!, $cartItems: [CartItemUpdateInput!]!){
       updateCartItems(
           input: {
               cart_id: $cartId,
               cart_items: $cartItems
           }
       )   {
           cart {
               id
               items {
                   uid
                   quantity
                   product {
                       sku
                   }
                   ... on GiftCardCartItem {
                       sender_name
                       sender_email
                       recipient_name
                       recipient_email
                       message
                       amount {
                           value
                           currency
                       }
                   }
               }
           }
       }
   }
   
   variables
   {
       "cartId": "sDrOu06VYlGejhDivQMcnmcNPSxTMUDd",
       "cartItems": [
           {
               "cart_item_id": 113,
               "quantity": 1,
               "customizable_options": [{
                       "uid": "Z2lmdGNhcmQvZ2lmdGNhcmRfc2VuZGVyX25hbWU=",
                       "value_string": "sender_name"
                   },
                   {
                       "uid": "Z2lmdGNhcmQvZ2lmdGNhcmRfc2VuZGVyX2VtYWls",
                       "value_string": "sender_email"
                   },
                   {
                       "uid": "Z2lmdGNhcmQvZ2lmdGNhcmRfcmVjaXBpZW50X25hbWU=",
                       "value_string": "recipient name"
                   },
                   {
                       "uid": "Z2lmdGNhcmQvZ2lmdGNhcmRfcmVjaXBpZW50X2VtYWls",
                       "value_string": "recipient_email"
                   },
                   {
                       "uid": "Z2lmdGNhcmQvZ2lmdGNhcmRfbWVzc2FnZQ==",
                       "value_string": "message"
                   },
                   {
                       "uid": "Z2lmdGNhcmQvY3VzdG9tX2dpZnRjYXJkX2Ftb3VudA==",
                       "value_string": "10"
                   }
               ]
           }]
   }
   ```

<u>Risultati previsti</u>:

Tutti i campi dei prodotti gift card (sender_name, sender_email, recipient_name, recipient_email, message, amount) vengono aggiornati tramite `updateCartItems` mutazione.

<u>Risultati effettivi</u>:

Viene aggiornato solo l’importo.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
