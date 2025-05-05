---
title: Impossibile salvare *contact* come chiave URL
description: Questo articolo fornisce una soluzione al problema quando non è possibile salvare *contact* come chiave URL (ad esempio, "/contact") per i prodotti o le pagine CMS. Quando tenti di salvare la chiave URL, ricevi un errore che indica che la chiave URL è un URL duplicato.
exl-id: eb340813-aba5-43a4-af5d-8fb64c93e021
feature: CMS, Marketing Tools, Storefront
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# Impossibile salvare *contatto* come chiave URL

Questo articolo fornisce una soluzione al problema quando non è possibile salvare *contact* come chiave URL (ad esempio, &quot;/contact&quot;) per prodotti o pagine CMS.

## Prodotti e versioni interessati

Adobe Commerce (tutti i metodi di distribuzione) 2.4.x

## Problema

Impossibile salvare un prodotto o una pagina CMS utilizzando il termine *contatto* come chiave URL. Quando tenti di salvare la chiave URL, ricevi un errore che indica che la chiave URL è un URL duplicato.

<u>Passaggi da riprodurre</u>:

Crea una pagina CMS con *contatto* come chiave URL.

<u>Risultato previsto</u>:

La pagina viene salvata con *contatto* come chiave URL.

<u>Risultato effettivo</u>:

Impossibile salvare la pagina. Errore: *Il valore specificato nel campo Chiave URL genererebbe un URL già esistente.*

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

Non è possibile utilizzare il termine *contatto* come chiave URL, tuttavia è possibile utilizzare il termine *contatto* combinato con un&#39;altra lettera o numero (ad esempio *contatto1* e *contatto2*). Anche se il termine non deve essere *contact+\&lt;altro numero o lettera\>*, potrebbe essere una stringa qualsiasi purché la lunghezza non superi i 255 caratteri.

Effettua le seguenti operazioni:

1. Accedi ad Amministratore Commerce.
1. Vai a **[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL URL Rewrites]**.
1. Fare clic su **[!UICONTROL Add URL Rewrite]**.
1. Selezionare *[!UICONTROL Custom]* nel menu a discesa [!UICONTROL Create URL Rewrite].
   1. In [!UICONTROL Request Path], digitare &quot;contact&quot;. [!UICONTROL Request Path] è ciò che un utente immette nel browser e [!UICONTROL Target Path] è il luogo in cui deve reindirizzare.
   1. In [!UICONTROL Target Path], digita la nuova chiave URL (ad esempio, &quot;contact1&quot;).
   1. Selezionare *[!UICONTROL No]* nel menu a discesa [!UICONTROL Redirect].

## Lettura correlata

* [L&#39;URL riscrive](https://experienceleague.adobe.com/it/docs/commerce-admin/marketing/seo/url-rewrites/url-rewrite) nella nostra guida utente.
* [Best practice per l&#39;ottimizzazione SEO](https://experienceleague.adobe.com/it/docs/commerce-admin/marketing/seo/seo-overview) nella guida utente.
