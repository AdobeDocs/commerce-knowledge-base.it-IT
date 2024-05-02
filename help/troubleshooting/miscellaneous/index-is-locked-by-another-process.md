---
title: Indice bloccato da un altro processo
description: Questo articolo parla di un problema di indicizzazione comune in Adobe Commerce, in cui l’indice è bloccato da un altro processo e saltato.
exl-id: 542c714c-fad5-4f0e-9757-d90044c36bfc
feature: Catalog Management, Categories
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# Indice bloccato da un altro processo

Questo articolo parla di un problema di indicizzazione comune in Adobe Commerce, in cui l’indice è bloccato da un altro processo e saltato.

## Prodotti e versioni interessati

* Adobe Commerce 2.X

## Problema

Durante una reindicizzazione completa nell’interfaccia CLI, Adobe Commerce visualizza il messaggio di errore: *&#39;L&#39;indice è bloccato da un altro processo di reindicizzazione. Ignorato.&#39;* In altre parole, quando il processo o il tipo di indice è bloccato, non è possibile reindicizzare quel particolare tipo di indice bloccato. La reindicizzazione salta sempre quel tipo di indice.

## Causa

Questo errore può verificarsi se l’indice precedente non è stato completato correttamente. Alcuni possibili motivi sono:

* Il processo è stato interrotto da un altro processo o utente.
* Limite di memoria.
* Errore MySQL, ad esempio timeout.
* Errore PHP irreversibile durante la reindicizzazione.

## Passaggi da riprodurre

1. Ad esempio, supponiamo che il    ```bash    cataloginventory_stock ```    tipo di indice bloccato.
1. Quando si tenta di reindicizzare tutti i dati eseguendo il comando CLI    ```bash    php bin/magento indexer:reindex    ```, si otterrà il seguente risultato:    ```bash    customer_grid index has been rebuilt successfully in 00:00:09    catalog_category_product index has been rebuilt successfully in 00:00:07    catalog_product_category index has been rebuilt successfully in 00:00:00    catalogrule_rule index has been rebuilt successfully in 00:00:05    catalog_product_attribute index has been rebuilt successfully in 00:00:04    cataloginventory_stock index is locked by another reindex process. Skipping.    catalog_product_price index has been rebuilt successfully in 00:00:01    catalogrule_product has been rebuilt successfully in 00:00:00    catalogsearch_fulltext index has been rebuilt successfully in 00:00:01    ```
1. Come si può vedere sopra, il    ```bash    cataloginventory_stock```    il processo di indicizzazione è stato ignorato.


## Soluzione

È necessario reimpostare lo stato dell&#39;indice, quindi provare a eseguire il nuovo processo di reindicizzazione. Per reimpostare lo stato dell’indice, è necessario eseguire il comando:

```bash
bin/magento indexer:reset <index identifier>
```

Se non sei sicuro di quali siano gli identificatori di indice (codice), puoi elencarli utilizzando il comando:

```bash
bin/magento indexer:info
```

Per completezza, ecco tutte le possibili combinazioni per gli indici nativi:

```bash
bin/magento indexer:reset design_config_grid;
bin/magento indexer:reset customer_grid;
bin/magento indexer:reset catalog_category_product;
bin/magento indexer:reset catalog_product_category;
bin/magento indexer:reset catalogrule_rule;
bin/magento indexer:reset catalog_product_attribute;
bin/magento indexer:reset cataloginventory_stock;
bin/magento indexer:reset catalog_product_price;
bin/magento indexer:reset catalogrule_product;
bin/magento indexer:reset catalogsearch_fulltext;
```


## Lettura correlata

Nella nostra knowledge base di supporto:

* [Le attività Cron bloccano le attività da altri gruppi (Adobe Commerce su infrastruttura cloud)](/help/troubleshooting/miscellaneous/cron-tasks-lock-tasks-from-other-groups.md)

Nella nostra guida utente:

* [Gestione indice](https://docs.magento.com/user-guide/system/index-management.html?itm_source=merchdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=reindexing)

Nella documentazione per gli sviluppatori:

* [Panoramica sull’indicizzazione](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/indexing.html)
* [Best practice per gli indicizzatori](https://devdocs.magento.com/guides/v2.3/performance-best-practices/configuration.html#indexers)
* [Configurare Ed Eseguire Cron](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-cron.html)
* [Gestire Gli Indicizzatori](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-index.html)
* [Ottimizzazione dell&#39;indicizzatore](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/indexer-batch.html)
