---
title: "MDVA-37748: la query GraphQL restituisce prodotti non assegnati a un catalogo condiviso"
description: La patch MDVA-37748 risolve il problema che causa la restituzione da parte di una query GraphQL di prodotti non assegnati a un catalogo condiviso. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.5. L'ID della patch è MDVA-37748. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
exl-id: 1f441882-dc14-433c-aa03-ff22483ce5a7
feature: B2B, GraphQL, Catalog Management, Categories, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# MDVA-37748: la query GraphQL restituisce prodotti non assegnati a un catalogo condiviso

La patch MDVA-37748 risolve il problema che causa la restituzione da parte di una query GraphQL di prodotti non assegnati a un catalogo condiviso. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.5. L&#39;ID della patch è MDVA-37748. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La query GraphQL restituisce prodotti non assegnati a un catalogo condiviso.

<u>Prerequisiti</u>:

I moduli B2B sono installati.

<u>Passaggi da riprodurre</u>:

1. Crea due prodotti e assegnali a una categoria:
   * Prodotto 1 - Pubblico
   * Prodotto 2

1. Assegna &quot;Prodotto 1 - Pubblico&quot; al catalogo condiviso &quot;Predefinito (Generale)&quot;.
1. Crea un catalogo condiviso personalizzato aggiuntivo e assegnalo al &quot;Prodotto 2&quot;.
1. Crea una nuova società e assegnala al catalogo condiviso aggiuntivo creato nel passaggio tre.
1. Dopo l’esecuzione/reindicizzazione cron, sul front-end, verifica di poter visualizzare &quot;Prodotto 1 - Pubblico&quot; se non hai effettuato l’accesso.
1. Accedi come amministratore della società creata nel passaggio quattro e verifica di visualizzare solo &quot;Prodotto 2&quot;.
1. Richiedi un token di autorizzazione utilizzando la seguente query GraphQL:

   <pre>
    <code class="language-graphql">
    mutation &lbrace;
      generateCustomerToken(
        email: "company.admin@exapmle.test"
        password: "password"
      ) &lbrace;
        token
      &rbrace;
    &rbrace;
    </code>
    </pre>

1. Aggiungi l&#39;intestazione **Valore-del-token** di Bearer autorizzazione ed esegui la seguente query GraphQL:

   <pre>
    <code class="language-graphql">
    &lbrace;
      products(
          filter: {},
          pageSize: 100,
          currentPage: 1
          sort: {}
        ) &lbrace;
          total_count
          page_info &lbrace;
            page_size
            current_page
          &rbrace;
          aggregations &lbrace;
            attribute_code
            count
            label
            options &lbrace;
              label
              value
              count
            &rbrace;
          &rbrace;
          items &lbrace;
            name
            sku
            created_at
            updated_at
            stock_status
            description {html}
            short_description {html}
            url_key
            url_path
            price_tiers&lbrace;
              final_price&lbrace;
                  value
                  currency
                &rbrace;
              discount&lbrace;
                  amount_off
                  percent_off
                &rbrace;
              quantity
            &rbrace;
            price_range &lbrace;
             maximum_price &lbrace;
              regular_price &lbrace;
                value
              &rbrace;
              final_price &lbrace;
                value
              &rbrace;
            &rbrace;
            minimum_price &lbrace;
              regular_price &lbrace;
                value
              &rbrace;
              final_price &lbrace;
               value
              &rbrace;
            &rbrace;
          &rbrace;
          image &lbrace;
           url
          &rbrace;
          thumbnail &lbrace;
           url
          &rbrace;
          small_image &lbrace;
           url
          &rbrace;
          media_gallery &lbrace;
           url
          &rbrace;
          ... on ConfigurableProduct &lbrace;
            configurable_options &lbrace;
             id

             label
             position
             use_default
             attribute_code
             values &lbrace;
               value_index
               label
               swatch_data &lbrace;
                 value
               &rbrace;
            &rbrace;
            product_id
          &rbrace;
          variants &lbrace;
            product &lbrace;
              id
              name
              sku
              &#x200B;#margin
              &#x200B;#margin_percentage
              image &lbrace;
                url
              &rbrace;
              small_image &lbrace;
                url
              &rbrace;
              thumbnail &lbrace;
                url
              &rbrace;
              media_gallery&lbrace;
                url
              &rbrace;
              attribute_set_id
              ... on PhysicalProductInterface &lbrace;
                weight
              &rbrace;
              price_range &lbrace;
                minimum_price &lbrace;
                  regular_price &lbrace;
                    value
                    currency
                  &rbrace;
                &rbrace;
              &rbrace;
            &rbrace;
            attributes &lbrace;
              label
              code
              value_index
            &rbrace;
          &rbrace;
        &rbrace;
      &rbrace;

    &rbrace;
&rbrace;
</code>
</pre>

<u>Risultati previsti</u>:

Il conteggio e il prodotto restituito da GraphQL considerano solo il prodotto assegnato al catalogo condiviso associato all’utente connesso.

<u>Risultati effettivi</u>:

Viene restituito solo &quot;Prodotto 2&quot;, ma `total_count` ne mostra due.

<pre>
<code class="language-graphql">
&lbrace;
  "data": &lbrace;
    "products": &lbrace;
      "total_count": 2,
      "page_info": &lbrace;
        "page_size": 100,
        "current_page": 1
      &rbrace;,
      "aggregations": &lbrack;
        &lbrace;
          "attribute_code": "price",
          "count": 2,
          "label": "Price",
          "options": &lbrack;
            &lbrace;
              "label": "0-100",
              "value": "0_100",
              "count": 1
            &rbrace;,
            &lbrace;
              "label": "100-200",
              "value": "100_200",
              "count": 1
            &rbrace;
          &rbrack;
        &rbrace;,
        &lbrace;
          "attribute_code": "category_id",
          "count": 1,
          "label": "Category",
          "options": &lbrack;
            &lbrace;
              "label": "Cat 1",
              "value": "3",
              "count": 2
            &rbrace;
          &rbrack;
        &rbrace;
      &rbrack;,
      "items": &lbrack;
        &lbrace;
          "name": "Product 2",
          "sku": "Product 2",
          "created_at": "2021-05-12 10:51:44",
          "updated_at": "2021-05-12 11:03:24",
          "stock_status": "IN_STOCK",
          "description": &lbrace;
            "html": ""
          &rbrace;,
          "short_description": &lbrace;
            "html": ""
          &rbrace;,
          "url_key": "product-2",
          "url_path": null,
          "price_tiers": &lbrack;
            &lbrace;
              "final_price": &lbrace;
                "value": 90,
                "currency": "USD"
              &rbrace;,
              "discount": &lbrace;
                "amount_off": 10,
                "percent_off": 10
              &rbrace;,
              "quantity": 1
            &rbrace;
          &rbrack;,
          "price_range": &lbrace;
            "maximum_price": &lbrace;
              "regular_price": &lbrace;
                "value": 100
              &rbrace;,
              "final_price": &lbrace;
                "value": 90
              &rbrace;
            &rbrace;,
            "minimum_price": &lbrace;
              "regular_price": &lbrace;
                "value": 100
              &rbrace;,
              "final_price": &lbrace;
                "value": 90
              &rbrace;
            &rbrace;
          &rbrace;,
          "image": &lbrace;
            "url": "../pub/static/version1620816308/frontend/Magento/luma/en_US/Magento_Catalog/images/product/placeholder/image.jpg"
          &rbrace;,
          "thumbnail": &lbrace;
            "url": "../pub/static/version1620816308/frontend/Magento/luma/en_US/Magento_Catalog/images/product/placeholder/thumbnail.jpg"
          &rbrace;,
          "small_image": &lbrace;
            "url": "../pub/static/version1620816308/frontend/Magento/luma/en_US/Magento_Catalog/images/product/placeholder/small_image.jpg"
          &rbrace;,
          "media_gallery": []
        &rbrace;
      &rbrack;
    &rbrace;
  &rbrace;
&rbrace;
</code>
</pre>

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
