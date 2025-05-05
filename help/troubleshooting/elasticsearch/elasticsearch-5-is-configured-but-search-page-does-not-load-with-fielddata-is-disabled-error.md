---
title: L'Elasticsearch 5 è configurato, ma la pagina di ricerca non viene caricata con l'errore "Dati campo è disabilitato..."
description: "Questo argomento descrive come risolvere il problema con l'Elasticsearch 5, in cui la pagina di ricerca non viene caricata e viene generata l'eccezione simile alla seguente:"
exl-id: f5fa8144-4e7c-45ce-89d0-a8367e91d6db
feature: Cache
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# L&#39;Elasticsearch 5 è configurato, ma la pagina di ricerca non viene caricata con l&#39;errore &quot;Dati campo è disabilitato...&quot;

Questo argomento descrive come risolvere il problema con l’Elasticsearch 5, in cui la pagina di ricerca non viene caricata e viene generata l’eccezione simile alla seguente:

```bash
{"0":"{\"error\":{\"root_cause\":[{\"type\":\"illegal_argument_exception\",\"reason\":\"Fielddata is disabled on text fields by default. Set fielddata=true on [%attribute_code%]] in order to load fielddata in memory by uninverting the inverted index. Note that this can however use significant memory.\"}].
```

## Versioni interessate

* Adobe Commerce 2.2.x
* Elasticsearch v.5

>[!NOTE]
>
>Elasticsearch v.5 è obsoleto per Adobe Commerce 2.3.x

## Problema

Prerequisiti: l’Elasticsearch 5 è configurato.

Nella richiesta di ricerca nei registri viene generata la seguente eccezione:

```bash
{"0":"{\"error\":{\"root_cause\":[{\"type\":\"illegal_argument_exception\",\"reason\":\"Fielddata is disabled on text fields by default. Set fielddata=true on [%attribute_code%]] in order to load fielddata in memory by uninverting the inverted index. Note that this can however use significant memory.\"}].
```

## Causa

Per impostazione predefinita, solo alcuni tipi di attributi di prodotto possono essere utilizzati nella navigazione a livelli. Sono Sì/No, A discesa, Selezione multipla e Prezzo. Per questo motivo, nell&#39;amministratore di Commerce non è possibile impostare un attributo di qualsiasi altro tipo come **Utilizzo nella navigazione a livelli** = *Filterable* o **Utilizzo nella navigazione a livelli dei risultati di ricerca** = *Sì*. Esiste tuttavia la possibilità tecnica di aggirare questo limite modificando direttamente i valori `is_filterable` e `is_filterable_in_search` nel database. In questo caso, e qualsiasi altro tipo di attributo, ad esempio Data, Testo e così via, è impostato per essere utilizzato in Navigazione a livelli, l&#39;Elasticsearch 5 genera un&#39;eccezione.

Per questo motivo, è necessario verificare se esistono attributi diversi da Menu a discesa, Selezione multipla e Prezzo impostati per l&#39;utilizzo in Navigazione a livelli. Eseguire la query seguente per cercare questi attributi:

```sql
SELECT ea.attribute_code, ea.frontend_input, cea.is_filterable, cea.is_filterable_in_search FROM eav_attribute AS ea
    -> INNER JOIN catalog_eav_attribute AS cea ON ea.attribute_id = cea.`attribute_id`
    -> WHERE (is_filterable = 1 OR is_filterable_in_search = 1) AND frontend_input NOT IN ('boolean', 'multiselect', 'select', 'price');
```

Il risultato conterrà un elenco di attributi utilizzati per la navigazione a livelli, il cui tipo non lo consente. Per risolvere il problema, segui i passaggi descritti nella sezione seguente.

## Soluzione

Per risolvere il problema, è necessario impostare `is_filterable` (ovvero, utilizzato in Navigazione a livelli) e `filterable_in_search` (ovvero, utilizzato nei risultati della ricerca Navigazione a livelli) su &quot;0&quot; (non utilizzato). A questo scopo, effettua le seguenti operazioni:

1. Creare un backup del database.
1. Utilizza uno strumento di database come [phpMyAdmin](https://experienceleague.adobe.com/it/docs/commerce-operations/installation-guide/prerequisites/optional-software#phpmyadmin) oppure accedi al database manualmente dalla riga di comando per eseguire la seguente query SQL:

   ```sql
   UPDATE catalog_eav_attribute AS cea
       INNER JOIN eav_attribute AS ea
           ON ea.attribute_id = cea.attribute_id
   SET cea.is_filterable = 0, cea.is_filterable_in_search = 0
   WHERE (cea.is_filterable = 1 OR cea.is_filterable_in_search = 1)
       AND frontend_input NOT IN ('boolean', 'multiselect', 'select', 'price');
   ```

1. Esegui la reindicizzazione completa della ricerca nel catalogo utilizzando il seguente comando:

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

1. Pulisci cache eseguendo

   ```bash
   bin/magento cache:clean
   ```

o nell&#39;amministratore di Commerce in **Sistema** > **Strumenti** > **Gestione cache**.

Ora dovresti essere in grado di eseguire ricerche nel catalogo senza problemi.
