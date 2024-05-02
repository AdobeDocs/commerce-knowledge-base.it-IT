---
title: Impossibile salvare *contact* come chiave URL
description: Questo articolo fornisce una soluzione al problema quando non è possibile salvare *contact* come chiave URL (ad esempio, "/contact") per i prodotti o le pagine CMS. Quando tenti di salvare la chiave URL, ricevi un errore che indica che la chiave URL è un URL duplicato.
exl-id: eb340813-aba5-43a4-af5d-8fb64c93e021
feature: CMS, Marketing Tools, Storefront
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# Impossibile salvare *contatto* come chiave URL

Questo articolo fornisce una soluzione al problema quando non è possibile salvare *contatto* come chiave URL (ad esempio, &quot;/contact&quot;) per prodotti o pagine CMS.

## Prodotti e versioni interessati

Adobe Commerce (tutti i metodi di distribuzione) 2.4.x

## Problema

Non è possibile salvare un prodotto o una pagina CMS utilizzando il termine *contatto* come chiave URL. Quando tenti di salvare la chiave URL, ricevi un errore che indica che la chiave URL è un URL duplicato.

<u>Passaggi da riprodurre</u>:

Creare una pagina CMS con *contatto* come chiave URL.

<u>Risultato previsto</u>:

La pagina viene salvata con *contatto* come chiave URL.

<u>Risultato effettivo</u>:

Impossibile salvare la pagina. Viene visualizzato l&#39;errore: *Il valore specificato nel campo Chiave URL genera un URL già esistente.*

## Causa

*Contatto* è una parola riservata definita in `vendor/magento/module-contact/view/frontend/layout/contact_index_index.xml`.

```xml
<router id="standard">
      <route id="contact" frontName="contact">
          <module name="Magento_Contact" />
      </route>
  </router>
```

## Soluzione

Non è possibile utilizzare il termine *contatto* come chiave URL, tuttavia, puoi utilizzare il termine *contatto* combinato con un&#39;altra lettera o numero (ad esempio, *contatto1* e *contatto2*). Anche se il termine non deve necessariamente essere *contatto+\&lt;another number=&quot;&quot; or=&quot;&quot; letter=&quot;&quot;>*, il termine potrebbe essere qualsiasi stringa purché la lunghezza non superi i 255 caratteri.

Effettua le seguenti operazioni:

1. Accedi ad Amministratore Commerce.
1. Vai a **[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL URL Rewrites]**.
1. Clic **[!UICONTROL Add URL Rewrite]**.
1. Seleziona *[!UICONTROL Custom]* il [!UICONTROL Create URL Rewrite] a discesa.
   1. In [!UICONTROL Request Path], digitare &quot;contact&quot;. Tieni presente che [!UICONTROL Request Path] è ciò che un utente immette nel browser e [!UICONTROL Target Path] è il punto in cui deve essere reindirizzato.
   1. In [!UICONTROL Target Path], digita la nuova chiave URL (ad esempio, &quot;contact1&quot;).
   1. Seleziona *[!UICONTROL No]* nel [!UICONTROL Redirect] a discesa.

## Lettura correlata

* [Riscritture URL](https://docs.magento.com/user-guide/marketing/url-rewrite.html) nella guida utente.
* [Best practice per l’ottimizzazione SEO](https://docs.magento.com/user-guide/marketing/seo-best-practices.html) nella guida utente.
