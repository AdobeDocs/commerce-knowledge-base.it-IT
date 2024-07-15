---
title: Gli indici invalidati e "indexer_reindex_all_invalid" vengono eseguiti costantemente
description: Gli indici invalidati e "indexer_reindex_all_invalid" vengono eseguiti costantemente
labels: troubleshooting,error,indexing,crons,site performance,adobe commerce,magento,cron,indexer_reindex_all_invalid,SQL,MySQL,reindex
exl-id: c7148ef4-2155-4d4c-869b-1d08de4af598
feature: B2B, Catalog Management, Categories, Observability, Price Indexer
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# Indici invalidati e `indexer_reindex_all_invalid` eseguiti costantemente

Questo articolo fornisce una possibile soluzione a questo problema quando il sito presenta problemi di prestazioni causati da una reindicizzazione costante. Ciò è dovuto all&#39;esecuzione continua del processo [!DNL cron] `indexer_reindex_all_invalid` e alla pulizia delle cache in [!DNL reindex].

## Prodotti e versioni interessati

* Adobe Commerce (cloud e on-premise) 2.4.0+ (poiché **[!UICONTROL Category Permissions]** è una funzionalità esclusiva di Adobe Commerce, non influirà sul Magento Open Source).

## Problema

In [!DNL New Relic One] i registri errori dovrebbero mostrare `indexer_update_all_views` in esecuzione molte volte con un tempo > 1 secondo (ovvero, sta elaborando qualcosa).

## Causa

Quando l’importazione core di Adobe Commerce viene eseguita (manualmente o da [!DNL cron]), viene eseguito un set di plug-in tra più moduli core per determinare quali indici devono essere invalidati.

Il problema si verifica quando il modulo **[!UICONTROL Category Permissions]** è abilitato in [!DNL Commerce Admin]. Se questo è vero, allora il plug-in del modulo invalida sempre gli indici di prodotto e categoria (e gli indici collegati) quando viene eseguita un’importazione. Se vengono esaminati i tipi di importazione standard, tutti influiscono su **[!UICONTROL Category Permissions]**. È previsto l’annullamento della validità.

Inoltre, quando un sito ha moduli B2B abilitati, se **[!UICONTROL Shared Catalog]** è attivato, si attiva e blocca **[!UICONTROL Category Permissions]**. La disattivazione di **[!UICONTROL Shared Catalog]** sbloccherà **[!UICONTROL Category Permissions]**, ma non lo spegnerà.

<u>Controllo dei registri [!DNL cron] nel database [!DNL MySQL]</u>:

Se accedi al tuo database [!DNL MySQL], potranno controllare il registro di `cron` per il processo **[!DNL reindex all indexes]**.
**dovrebbe** comparire molte volte, ma il fattore importante è che il processo fa una delle due cose possibili.

Il processo può eseguire solo una di queste due operazioni:

1. Niente: ci vorrebbe da 0 a 1 secondo (un secondo o meno) - il processo controlla per vedere se deve fare qualcosa e poi si interrompe se non ha bisogno di fare nulla.
1. [!DNL Reindex] tutto: ci vorrà sempre del tempo, in genere minuti.

Normalmente si desidera visualizzare molte occorrenze del processo, ma con un tempo di esecuzione inferiore a 1 secondo.
Un commerciante può quindi utilizzare questa query [!DNL MySQL] per trovare le transazioni che richiedono **più di 1 secondo** per l&#39;esecuzione:

```sql
SELECT TIMESTAMPDIFF(SECOND, executed_at, finished_at) AS period FROM cron_schedule WHERE job_code = 'indexer_reindex_all_invalid' HAVING period > 1
```

Puoi vedere per quanto tempo viene registrato un periodo eseguendo:

```sql
SELECT executed_at FROM cron_schedule WHERE job_code = 'indexer_reindex_all_invalid' AND executed_at IS NOT NULL ORDER BY executed_at ASC LIMIT 1;
```

Se non si dispone di un periodo di tempo sufficiente per effettuare una valutazione corretta, è possibile aumentare il tempo di conservazione di un processo `cron` completato nel registro dopo questa guida [[!DNL Cron] (attività pianificate)](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) e aumentare il valore **[!DNL Success History Lifetime]** (il valore predefinito è solo 60 minuti).


## Soluzione

Estendere `Magento\CatalogPermissions\Model\Indexer\Plugin\Import` in modo che il metodo `afterImportSource` escluda l&#39;importazione personalizzata.

```
    public function afterImportSource(\Magento\ImportExport\Model\Import $subject, $import)
    {
        if ($this->config->isEnabled() && $subject->getEntity() !== 'ENTITY_CODE') {
            $this->indexerRegistry->get(\Magento\CatalogPermissions\Model\Indexer\Category::INDEXER_ID)->invalidate();
            $this->indexerRegistry->get(\Magento\CatalogPermissions\Model\Indexer\Product::INDEXER_ID)->invalidate();
        }
        return $import;
    }
```

Dove `ENTITY_CODE` è il valore utilizzato per il parametro del nome entità nel file `import.xml` per l&#39;importazione personalizzata.

## Lettura correlata

[Configura [!DNL cron] processi](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) nella Guida alla configurazione delle operazioni di Adobe Commerce.
