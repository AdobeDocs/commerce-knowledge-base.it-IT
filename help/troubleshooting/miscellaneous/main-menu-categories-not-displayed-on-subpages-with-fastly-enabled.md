---
title: Menu principale (Categorie) non visualizzato nelle pagine secondarie con Fastly abilitato
description: Questo articolo fornisce una correzione per quando il menu principale (o il [menu di navigazione superiore per le categorie](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html) nella nostra guida utente) non viene visualizzato nella vetrina per le pagine secondarie (ad esempio, *blog/pagina*) quando Fastly o Varnish è abilitato.
exl-id: 7c54791d-8aa6-4f01-a28b-a7aecdb8ff74
feature: Categories, Marketing Tools
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# Menu principale (Categorie) non visualizzato nelle pagine secondarie con Fastly abilitato

Questo articolo fornisce una correzione per quando il menu principale (o il [menu di navigazione superiore per categorie](/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html) nella guida utente) non viene visualizzato in vetrina per le pagine secondarie (ad esempio, *blog/pagina*) quando Fastly o Varnish è abilitato.

**Causa:** il carattere `/` (barra) non consentito nel parametro *Chiave URL* della pagina (impostazioni di ottimizzazione motore di ricerca). Il carattere viene in genere aggiunto quando il percorso *URL* (con l&#39;intera posizione della pagina) viene erroneamente specificato al posto della *chiave URL*: ad esempio, *blog/pagina\_name* invece di solo *pagina\_name*.

**Soluzione:** rimuovere il carattere `/` (barra). Per il parametro *Chiave URL*, specificare solo il nome della pagina.

## Versioni interessate

* Adobe Commerce on-premise 2.X.X
* Adobe Commerce sull’infrastruttura cloud 2.X.X
* Fastly o vernice

## Problema

Il menu principale (indicato anche come [menu di navigazione superiore categoria](/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html) nella guida utente) non viene visualizzato nella vetrina per le pagine secondarie quando sono abilitati i servizi Fastly o altri servizi basati su Vernice.

## Causa

Il problema è causato dal carattere non consentito `/` (barra), aggiunto al parametro *Chiave URL* (impostazioni di ottimizzazione motore di ricerca).

Il carattere viene in genere aggiunto quando *Percorso URL* (con posizione dell&#39;intera pagina, inclusa la risorsa/directory padre della pagina) viene erroneamente specificato al posto di *Chiave URL*: ad esempio, *blog/pagina\_name* invece di solo *pagina\_name*.

![Parametro chiave URL per impostazioni SEO](assets/seo_url_key.png)

## Soluzione

Rimuovi il carattere `/` (barra) dal parametro *Chiave URL* per tutte le pagine dell&#39;archivio.

In altre parole, utilizza *Chiave URL* invece di *Percorso URL*: menziona solo il nome della pagina senza alcuna risorsa/directory principale.

### Recommendations nella gerarchia delle pagine e SEO (Search Engine Optimization)

Per impostare la gerarchia di pagine, utilizzare la sezione **Gerarchia** del menu Modifica pagina.

![Impostazioni gerarchia](assets/hierarchy_hr.png)

È inoltre possibile utilizzare il menu **Contenuto** > **Elementi** > **Gerarchia** per soluzioni gerarchiche più complesse.

Ai fini SEO sulle pagine dei prodotti, utilizza URL Rewrite (**Marketing** > **SEO &amp; Search** > **URL Rewrite**).

## Ulteriori informazioni nella guida utente

Il parametro *Chiave URL* per SEO:

* [Ottimizzazione motore di ricerca](/docs/commerce-admin/catalog/categories/create/categories-search-engine-optimization.html)
* [Aggiunta di una nuova pagina](/docs/commerce-admin/content-design/elements/pages/page-add.html)

Gerarchia pagine:

* [Panoramica](/docs/commerce-admin/content-design/elements/pages/page-hierarchy.html)
* [Aggiunta di un nodo](/docs/commerce-admin/content-design/elements/pages/page-hierarchy.html#add-a-hierarchy-node)
