---
title: Prestazioni lente a causa di pagine non memorizzabili in cache
description: Questo articolo fornisce soluzioni per l’aumento dei tempi di caricamento dei siti web o delle interruzioni dovute alla disattivazione della cache di pagina completa (ad esempio Fastly) per qualsiasi blocco su qualsiasi pagina/e che deve essere memorizzata in cache.
exl-id: 7401d9bd-710c-4221-9c3d-d78042c1c1ad
feature: Cache, Categories
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# Prestazioni lente a causa di pagine non memorizzabili in cache

Questo articolo fornisce soluzioni per l’aumento dei tempi di caricamento dei siti web o delle interruzioni dovute alla disattivazione della cache di pagina completa (ad esempio Fastly) per qualsiasi blocco su qualsiasi pagina/e che deve essere memorizzata in cache.

## Prodotti e versioni interessati

* Adobe Commerce sull’infrastruttura cloud 2.x.x
* Adobe Commerce on-premise 2.x.x

### Problema

Le prestazioni del sito risultano rallentate perché nelle pagine sono presenti blocchi di cache che devono essere memorizzabili in cache ma che sono stati impostati su `cacheable="false"` .

### Causa

Alcune pagine devono essere memorizzate nella cache da Adobe Commerce. Queste pagine hanno il throughput più elevato. Ogni richiesta di questi tipi di pagine non dalla cache rallenta le prestazioni di Adobe Commerce.

Queste pagine sono:

* Categoria catalogo (PLP)
* Pagina dettagli prodotto (PDP)
* Pagine di contenuti statici (home page, contattaci, ecc.)

I termini &quot;memorizzabile in cache&quot; e &quot;non memorizzabile in cache&quot; indicano se una pagina deve essere memorizzata in cache o meno. Per impostazione predefinita, tutte le pagine sono memorizzabili in cache. Tuttavia, se qualsiasi blocco in un layout è designato come non memorizzabile in cache, l’intera pagina non è memorizzabile in cache.

La schermata seguente mostra un blocco con un’impostazione `cacheable="false”`  ** ** che crea una pagina non memorizzabile in cache.

![non_cache_kb.png](assets/non_cacheable_kb.png)

Esempi di pagine non memorizzabili in cache includono prodotti di confronto, carrello e pagine di pagamento.

I seguenti elenchi di pagine non vengono memorizzati in cache (le cache Fastly, Block e Layout vengono evitate). Ciò si verifica a causa della configurazione &quot;memorizzabile in cache&quot; nel layout.

### Soluzione

Verifica se i file specificati sopra hanno l’impostazione `cacheable="false”` . In caso affermativo, controlla se questa impostazione è necessaria o richiesta.

* Se necessario, puoi spostare i blocchi non memorizzabili in cache in [meccanismo di contenuti privati](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/cache/page-caching/private-content.html?itm_source=devdocs&amp;itm_medium=quick_search&amp;itm_campaign=federated_search&amp;itm_term=private%20co) invece.
* Se non è necessario, rimuovere l&#39;attributo `cacheable="false”` e svuotare la cache di layout.

>[!NOTE]
>
>Per Adobe Commerce su infrastruttura cloud 2.4.1 e versioni successive, puoi utilizzare [Strumento di analisi a livello di sito](https://docs.magento.com/user-guide/reports/site-wide-analysis-tool.html) per verificare automaticamente se la cache della pagina intera non è configurata correttamente.

### Lettura correlata

[Panoramica della cache di Adobe Commerce](https://devdocs.magento.com/guides/v2.3/frontend-dev-guide/cache_for_frontdevs.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=cacheable%2) nella documentazione per gli sviluppatori.
