---
title: Impossibile salvare la spedizione come chiave URL
description: Questo articolo fornisce una soluzione al problema quando non è possibile salvare la spedizione come chiave URL (_ad esempio, /shipping_) per i prodotti o le pagine CMS. Quando tenti di salvare la chiave URL, ricevi un errore che indica che la chiave URL è un URL duplicato.
exl-id: df19b597-f615-4b19-82c1-59cc179fa720
feature: Marketing Tools, Shipping/Delivery, Storefront
role: Admin
source-git-commit: 1ce963142a261a17e2b42f79dd567c8484ec5b3e
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# Impossibile salvare _spedizione_ come chiave URL

Questo articolo fornisce una soluzione al problema quando non è possibile salvare la spedizione come chiave URL (_ad es. /shipping_) per prodotti o pagine CMS. Quando tenti di salvare la chiave URL, ricevi un errore che indica che la chiave URL è un URL duplicato.

## Prodotti e versioni interessati

Adobe Commerce (tutti i metodi di distribuzione) 2.4.x

## Problema

Impossibile salvare una pagina CMS con il termine _spedizione_ nella chiave URL.

<u>Passaggi da riprodurre</u>:

Creare un **[!UICONTROL CMS page]** con la chiave URL come _spedizione_.

<u>Risultato previsto</u>:

La pagina viene salvata con _spedizione_ come chiave URL.

<u>Risultato effettivo</u>:

Impossibile salvare in quanto si verifica questo errore:
*Il valore specificato nel campo Chiave URL genera un URL già esistente.*

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

Non è possibile utilizzare il termine _spedizione_ nella chiave URL, ma puoi utilizzare il termine _spedizione_ combinato con un&#39;altra lettera o numero (_Ad esempio, shipping1 e shipping2_).

Anche se il termine non deve necessariamente essere _spedizione_+&lt;another number=&quot;&quot; or=&quot;&quot; letter=&quot;&quot;> - il termine potrebbe essere qualsiasi stringa purché la lunghezza non superi *255* caratteri.

## Effettua le seguenti operazioni:

1. Accedi ad Adobe Commerce Admin.
1. Vai a **[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL URL Rewrites]**.
1. Clic **[!UICONTROL Add URL Rewrite]**.
1. Seleziona **[!UICONTROL Custom]** nel **[!UICONTROL Create URL Rewrite]** a discesa.
   1. Digita il [!UICONTROL Request Path] as **_spedizione_**.
   1. In **[!UICONTROL Target Path]**, digita la nuova chiave URL (_Ad esempio, &quot;shipping1&quot;_).
   1. Seleziona **[!UICONTROL No]** nel **[!UICONTROL Redirect]** a discesa.


      (**Nota**: il Percorso della richiesta è ciò che un utente immette nel browser e il Percorso di destinazione è il punto in cui deve reindirizzare.

Inoltre, evita di utilizzare queste parole chiave etichettate come *riservato* parole chiave che causano la visualizzazione della stessa eccezione. L’utilizzo di una qualsiasi delle parole chiave elencate di seguito come valore chiave URL causerà la visualizzazione dello stesso errore.


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

* [Riscritture URL](https://docs.magento.com/user-guide/marketing/url-rewrite.html) nella nostra Guida utente su merchandising e promozioni.
* [Best practice per l’ottimizzazione SEO](https://docs.magento.com/user-guide/marketing/seo-best-practices.html) nella nostra Guida utente su merchandising e promozioni.
