---
title: "ACSD-53148: due richieste parallele in GraphQL per l’aggiunta dello stesso prodotto configurabile"
description: Applica la patch ACSD-53148 per risolvere il problema di Adobe Commerce, in cui due richieste parallele in GraphQL per l’aggiunta dello stesso prodotto configurabile al carrello hanno prodotto due elementi separati sul carrello con lo stesso SKU del prodotto.
feature: GraphQL, Shopping Cart
role: Admin, Developer
exl-id: 14290c7f-9b0a-4745-a579-5c34799b78ef
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# ACSD-53148: due richieste parallele in GraphQL per aggiungere lo stesso prodotto configurabile

La patch ACSD-53148 risolve il problema che, in seguito a due richieste parallele in GraphQL per l’aggiunta dello stesso prodotto configurabile al carrello, risultavano in due articoli separati sul carrello con lo stesso SKU del prodotto. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.37. L’ID della patch è ACSD-53148. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Due richieste parallele in GraphQL per l’aggiunta dello stesso prodotto configurabile al carrello hanno prodotto due elementi separati sul carrello con lo stesso SKU del prodotto.

<u>Passaggi da riprodurre</u>:

1. Creare un prodotto configurabile con SKU *Test* e un prodotto semplice con SKU *Test-A*.
1. Crea un nuovo carrello vuoto tramite GraphQL (cambia la posizione con il tuo [!DNL URL]):

   ```GraphQL
   curl --location 'http://mag.local/graphql' \
   --header 'Store: default' \
   --header 'Content-Type: application/json' \
   --data '{"query":"mutation{\n createEmptyCart\n}","variables"{}}'
   ```

1. Esegui due richieste simultanee per aggiungere lo stesso prodotto al carrello (modifica *cartID* e percorso per entrambe le richieste):

   ```GraphQL
       curl --location 'http://mag.local/graphql' --header 'Store: default' --header 'Content-Type: application/json' --data '{"query":"mutation($cartId: String!, $preSku: String!, $preParentSku: String!) {\r\n addConfigurableProductsToCart(\r\n input: {\r\n cart_id: $cartId\r\n cart_items: [\r\n {\r\n parent_sku: $preParentSku\r\n data: {\r\n quantity: 1\r\n sku: $preSku\r\n }\r\n }\r\n ]\r\n }\r\n ) {\r\n cart {\r\n items {\r\n id\r\n product {\r\n name\r\n sku\r\n }\r\n quantity\r\n \r\n prices {\r\n price {\r\n value\r\n currency\r\n }\r\n }\r\n ... on ConfigurableCartItem {\r\n configurable_options {\r\n option_label\r\n value_label\r\n }\r\n }\r\n }\r\n total_quantity\r\n prices {\r\n grand_total {\r\n value\r\n currency\r\n }\r\n discounts {\r\n amount {\r\n value\r\n currency\r\n }\r\n label\r\n }\r\n subtotal_excluding_tax {\r\n value\r\n currency\r\n }\r\n } \r\n }\r\n }\r\n}","variables":{"cartId":"VV85vRfmCrRm0aKLKkNDrXH2S5y7sSpf","preParentSku":"Test","preSku":"Test-A"}}' & curl --location 'http://mag.local/graphql' --header 'Store: default' --header 'Content-Type: application/json' --data '{"query":"mutation($cartId: String!, $preSku: String!, $preParentSku: String!) {\r\n addConfigurableProductsToCart(\r\n input: {\r\n cart_id: $cartId\r\n cart_items: [\r\n {\r\n parent_sku: $preParentSku\r\n data: {\r\n quantity: 1\r\n sku: $preSku\r\n }\r\n }\r\n ]\r\n }\r\n ) {\r\n cart {\r\n items {\r\n id\r\n product {\r\n name\r\n sku\r\n }\r\n quantity\r\n \r\n prices {\r\n price {\r\n value\r\n currency\r\n }\r\n }\r\n ... on ConfigurableCartItem {\r\n configurable_options {\r\n option_label\r\n value_label\r\n }\r\n }\r\n }\r\n total_quantity\r\n prices {\r\n grand_total {\r\n value\r\n currency\r\n }\r\n discounts {\r\n amount {\r\n value\r\n currency\r\n }\r\n label\r\n }\r\n subtotal_excluding_tax {\r\n value\r\n currency\r\n }\r\n } \r\n }\r\n }\r\n}","variables":{"cartId":"VV85vRfmCrRm0aKLKkNDrXH2S5y7sSpf","preParentSku":"Test","preSku":"Test-A"}}'
   ```

1. Ottieni il carrello per visualizzare gli elementi (cambia *cartId* e il percorso):

   ```GraphQL
   curl --location 'http://mag.local/graphql' \
   --header 'Store: default' \
   --header 'Content-Type: application/json' \
   --data '{"query":"{\n cart(cart_id: \"VV85vRfmCrRm0aKLKkNDrXH2S5y7sSpf\") {\n items {\n id\n product {\n name\n sku\n }\n quantity\n }\n\n }\n}\n","variables":{}}'
   ```

<u>Risultati previsti</u>:

Elemento elencato una volta con [!UICONTROL qty] = 2.

```GraphQL
    {"data":{"cart":{"items":[{"id":"5","product":{"name":"config1","sku":"config1"},"quantity":2}]}}}%
```

<u>Risultati effettivi</u>:

Elemento elencato due volte con [!UICONTROL qty] = 1.

```GraphQL
    {"data":{"cart":{"items":[{"id":"1","product":
    {"name":"config1","sku":"config1"},"quantity":1},
    {"id":"3","product":{"name":"config1","sku":"config1"},"quantity":1}]}}}%
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
