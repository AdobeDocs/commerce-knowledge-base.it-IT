---
title: "ACSD-52921: errore durante la richiesta dei dettagli del carrello a GraphQL per un prodotto configurabile esaurito"
description: Applica la patch ACSD-52921 per risolvere il problema di Adobe Commerce in cui si verifica un errore interno nel richiedere i dettagli del carrello a GraphQL per un prodotto configurabile esaurito.
feature: GraphQL, Configuration, Products, Shopping Cart
role: Admin
exl-id: 687460c4-f0d5-45d2-82b1-dda2947fe1e7
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-52921: errore nella richiesta dei dettagli del carrello a GraphQL per un prodotto configurabile esaurito

La patch ACSD-52921 risolve il problema che si verifica in caso di errore interno nel richiedere i dettagli del carrello a GraphQL per un prodotto configurabile esaurito. Questa patch è disponibile quando [!DNL Quality Patches Tool (QPT)] 1.1.35. L’ID della patch è ACSD-52921. Il problema è stato risolto in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Si verifica un errore interno nel richiedere i dettagli del carrello a GraphQL per un prodotto configurabile esaurito.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto configurabile con alcune opzioni.
1. Aggiungi un’opzione per il prodotto configurabile di cui sopra al carrello dal front-end (pagamento guest).
1. Ottieni `[ masked_id ]` dal `[ quote_id_mask ]` tabella db per l&#39;offerta creata sopra.
1. Esegui la seguente query GraphQL per ottenere i dettagli del carrello guest indicati sopra.

   Aggiungi il `[ masked_id ]` ricevuto dal passaggio 3 nella query.

   ```GraphQL
   {
       cart(cart_id: "masked_id") {
           items {
               product {
                   name
                   sku
               }
               ... on ConfigurableCartItem {
                   configurable_options {
                       configurable_product_option_uid
                       option_label
                       configurable_product_option_value_uid
                       value_label
                   }
               }
               quantity
               errors {
                   code
                   message
               }
           }
       }
   }   
   ```

1. In questo modo verranno restituiti i dettagli del preventivo senza alcun problema.
1. Vai al back-end e aggiorna i *[!UICONTROL Stock Status]* a *[!UICONTROL Out of Stock]*.
1. Esegui la stessa query GraphQL, come fatto nel passaggio 4.

<u>Risultati previsti</u>:

Il messaggio di errore viene inviato/trattato correttamente nella risposta.

<u>Risultati effettivi</u>:

*500 server interno* viene generato un errore in risposta alla query GraphQL.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
