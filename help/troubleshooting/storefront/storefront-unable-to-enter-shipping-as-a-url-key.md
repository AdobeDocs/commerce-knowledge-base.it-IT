---
title: Impossibile salvare la spedizione come chiave URL
description: Questo articolo fornisce una soluzione alternativa al problema quando non è possibile salvare la "spedizione" come chiave URL (ad esempio, "/shipping") per i prodotti o le pagine CMS. Quando tenti di salvare la chiave URL, ricevi un errore che indica che la chiave URL è un URL duplicato.
exl-id: df19b597-f615-4b19-82c1-59cc179fa720
feature: Marketing Tools, Shipping/Delivery, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# Impossibile salvare la spedizione come chiave URL

Questo articolo fornisce una soluzione alternativa al problema quando non è possibile salvare la &quot;spedizione&quot; come chiave URL (ad esempio, &quot;/shipping&quot;) per i prodotti o le pagine CMS. Quando tenti di salvare la chiave URL, ricevi un errore che indica che la chiave URL è un URL duplicato.

## Prodotti e versioni interessati

Adobe Commerce (tutti i metodi di distribuzione) 2.4.x

## Problema

Non puoi salvare una pagina CMS con il termine &quot;spedizione&quot; nella chiave URL.

<u>Passaggi da riprodurre</u>:

Crea una pagina CMS con la chiave URL &quot;shipping&quot;.

<u>Risultato previsto</u>:

La pagina viene salvata con &quot;shipping&quot; nella chiave URL.

<u>Risultato effettivo</u>:

Non è possibile salvare e viene visualizzato un errore: *Il valore specificato nel campo Chiave URL genera un URL già esistente.*

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

Non puoi utilizzare il termine &quot;spedizione&quot; nella chiave URL, ma puoi utilizzare il termine &quot;spedizione&quot; combinato con un’altra lettera o numero (ad esempio, &quot;spedizione1&quot; e &quot;spedizione2&quot;). Anche se il termine non deve essere &quot;spedizione&quot;+&lt;another number=&quot;&quot; or=&quot;&quot; letter=&quot;&quot;> - il termine potrebbe essere qualsiasi stringa purché la lunghezza non superi i 255 caratteri.

Effettua le seguenti operazioni:

1. Accedi all’amministratore di Commerce.
1. Vai a **Marketing** > SEO e ricerca > **Riscritture URL**.
1. Clic **Aggiungi riscrittura URL**.
1. Seleziona *Personalizzato* nel menu a discesa Crea URL Riscrittura.
   1. Digita nel Percorso richiesta &quot;shipping&quot;. Nota: il Percorso richiesta è ciò che un utente immette nel browser e il Percorso di destinazione è il punto in cui deve reindirizzare.
   1. Digita nel Percorso di destinazione la nuova chiave URL (ad esempio, &quot;shipping1&quot;).
   1. Seleziona **No** nel menu a discesa Reindirizza.

## Lettura correlata

* [Riscritture URL](https://docs.magento.com/user-guide/marketing/url-rewrite.html) nella guida utente.
* [Best practice per l’ottimizzazione SEO](https://docs.magento.com/user-guide/marketing/seo-best-practices.html) nella guida utente.
