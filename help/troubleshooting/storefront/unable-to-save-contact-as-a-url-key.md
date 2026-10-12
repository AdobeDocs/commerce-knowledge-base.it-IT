---
title: Impossibile salvare *contact* come chiave URL
description: Questo articolo fornisce una soluzione al problema quando non è possibile salvare *contact* come chiave URL (ad esempio, "/contact") per i prodotti o le pagine CMS. Quando tenti di salvare la chiave URL, ricevi un errore che indica che la chiave URL è un URL duplicato.
exl-id: eb340813-aba5-43a4-af5d-8fb64c93e021
feature: CMS, Marketing Tools, Storefront
role: Admin
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: ddbd0f6e-b569-5a04-8a70-55058777c373
    internal-label: CMS
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '350'
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

* [L&#39;URL riscrive](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/seo/url-rewrites/url-rewrite) nella nostra guida utente.
* [Best practice per l&#39;ottimizzazione SEO](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/seo/seo-overview) nella guida utente.
