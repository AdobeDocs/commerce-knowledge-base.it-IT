---
title: "ACSD-57846: i prodotti GraphQL cercano con il filtro prezzi zero che non restituiscono risultati"
description: Applica la patch ACSD-57846 per risolvere il problema di Adobe Commerce, in cui filtrando i prodotti a prezzo da zero si genera una richiesta non valida a  [!DNL OpenSearch]  e non si restituiscono risultati.
feature: GraphQL, Products
role: Admin, Developer
source-git-commit: 490c7449761ded6aef10a838f27e1ea7671c6cc8
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---


# ACSD-57846: GraphQL prodotti ricerca con filtro per zero prezzi non restituisce risultati

La patch di ACSD-57846 risolve il problema per cui filtrando i prodotti a prezzo da zero si genera una richiesta non valida a [!DNL OpenSearch] e non restituisce alcun risultato. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49. L’ID della patch è ACSD-57846. Il problema è stato risolto in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.6-p7

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il filtraggio dei prodotti a un prezzo da zero in una ricerca di prodotti GraphQL genera una richiesta non valida a [!DNL OpenSearch] e non restituisce alcun risultato.

<u>Passaggi da riprodurre</u>:

1. Crea una categoria con due prodotti semplici:
   * simple1 - prezzo $0
   * simple2 - prezzo $10
1. Assicurati che entrambi i prodotti siano visibili sul front-end.
1. Invia una richiesta con `price:{from:"1"}`.

   ```graphql
   query {
     products(
       pageSize: 50
       currentPage: 1,
       filter: {price:{from:"1"}}
     ) {
       totalResult: total_count
       productItems: items {
         sku
         urlKey: url_key
         price: price_range {
           fullPrice: minimum_price {
             finalPrice: final_price {
               currency
               value
             }
           }
         }
       }
     }
   }
   ```

1. Restituisce il prodotto, *simple2*.
1. Ora invia una richiesta con `price:{from:"0"}`.

   ```graphql
   query {
     products(
       pageSize: 50
       currentPage: 1,
       filter: {price:{from:"0"}}
     ) {
       totalResult: total_count
       productItems: items {
         sku
         urlKey: url_key
         price: price_range {
           fullPrice: minimum_price {
             finalPrice: final_price {
               currency
               value
             }
           }
         }
       }
     }
   }
   ```

<u>Risultati previsti</u>:

Entrambi i prodotti, *simple1* e *simple2*, vengono restituiti.

<u>Risultati effettivi</u>:

Nessun prodotto restituito.

```json
{
    "data": {
        "products": {
            "totalResult": 0,
            "productItems": []
        }
    }
}
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
