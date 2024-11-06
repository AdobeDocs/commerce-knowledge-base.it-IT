---
title: Impossibile salvare la spedizione come chiave URL
description: Questo articolo fornisce una soluzione al problema quando non è possibile salvare la spedizione come chiave URL (_ad esempio, /shipping_) per i prodotti o le pagine CMS. Quando tenti di salvare la chiave URL, ricevi un errore che indica che la chiave URL è un URL duplicato.
exl-id: df19b597-f615-4b19-82c1-59cc179fa720
feature: Marketing Tools, Shipping/Delivery, Storefront
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# Impossibile salvare _shipping_ come chiave URL

Questo articolo fornisce una soluzione al problema quando non è possibile salvare la spedizione come chiave URL (_ad esempio, /shipping_) per i prodotti o le pagine CMS. Quando tenti di salvare la chiave URL, ricevi un errore che indica che la chiave URL è un URL duplicato.

## Prodotti e versioni interessati

Adobe Commerce (tutti i metodi di distribuzione) 2.4.x

## Problema

Non puoi salvare una pagina CMS con il termine _shipping_ nella chiave URL.

<u>Passaggi da riprodurre</u>:

Crea un **[!UICONTROL CMS page]** con la chiave URL come _shipping_.

<u>Risultato previsto</u>:

La pagina viene salvata con _shipping_ come chiave URL.

<u>Risultato effettivo</u>:

Impossibile salvare in quanto si verifica questo errore:
*Il valore specificato nel campo Chiave URL genererebbe un URL già esistente.*

## Causa

Spedizione è una parola riservata definita in `vendor/magento/module-shipping/etc/frontend/routes.xml`.

```xml
<router id="standard">
      <route id="shipping" frontName="shipping">
          <module name="Magento_Shipping" />
      </route>
  </router>
```

## Soluzione

Non puoi usare il termine _shipping_ nella chiave URL, ma puoi usare il termine _shipping_ combinato con un&#39;altra lettera o numero (_Ad esempio shipping1 e shipping2_).

Anche se il termine non deve essere _shipping_+&lt;altro numero o lettera>, potrebbe essere una stringa qualsiasi purché la lunghezza non superi *255* caratteri.

## Effettua le seguenti operazioni:

1. Accedi ad Adobe Commerce Admin.
1. Vai a **[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL URL Rewrites]**.
1. Fare clic su **[!UICONTROL Add URL Rewrite]**.
1. Selezionare **[!UICONTROL Custom]** nel menu a discesa **[!UICONTROL Create URL Rewrite]**.
   1. Digitare [!UICONTROL Request Path] come **_spedizione_**.
   1. In **[!UICONTROL Target Path]** digitare la nuova chiave URL (_Ad esempio, &quot;shipping1&quot;_).
   1. Selezionare **[!UICONTROL No]** nel menu a discesa **[!UICONTROL Redirect]**.


      (**Nota**: il percorso della richiesta è ciò che un utente immette nel browser e il percorso di destinazione è il punto in cui deve reindirizzare.)

Inoltre, evita di usare queste parole chiave etichettate come *parole chiave riservate* che causano la visualizzazione della stessa eccezione. L’utilizzo di una qualsiasi delle parole chiave elencate di seguito come valore chiave URL causerà la visualizzazione dello stesso errore.


```
"admin"
"adminAnalytics"
"analytics"
"api"
"backup"
"bulk"
"captcha"
"catalog"
"catalogsearch"
"checkout"
"cms"
"contact"
"cookie"
"customer"
"directory"
"downloadable"
"giftmessage"
"groupedProduct"
"indexer"
"instantpurchase"
"loginascustomer"
"marketplace"
"mui"
"multishipping"
"newsletter"
"oauth"
"paypal"
"persistent"
"productalert"
"releaseNotification"
"reports"
"review"
"robots"
"rss"
"sales"
"search"
"security"
"sendfriend"
"shipping"
"stores"
"swagger"
"swatches"
"tax"
"theme"
"translation"
"vault"
"wishlist"
```

## Lettura correlata

* [URL riscrive](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/seo/url-rewrites/url-rewrite) nella guida utente per merchandising e promozioni.
* [Best practice per l&#39;ottimizzazione SEO](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/seo/seo-overview) nella guida utente per merchandising e promozioni.
