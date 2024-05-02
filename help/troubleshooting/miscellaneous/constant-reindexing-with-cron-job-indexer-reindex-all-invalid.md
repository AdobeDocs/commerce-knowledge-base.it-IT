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

# Indici invalidati e `indexer_reindex_all_invalid` esegui costantemente

Questo articolo fornisce una possibile soluzione a questo problema quando il sito presenta problemi di prestazioni causati da una reindicizzazione costante. Ciò è causato dalla [!DNL cron] processo `indexer_reindex_all_invalid` esecuzione continua e pulitura cache attiva [!DNL reindex].

## Prodotti e versioni interessati

* Adobe Commerce (cloud e on-premise) 2.4.0+ (As **[!UICONTROL Category Permissions]** è una funzione esclusiva di Adobe Commerce, non influisce sul Magento Open Source.)

## Problema

In entrata [!DNL New Relic One] i registri di errore dovrebbero essere visualizzati `indexer_update_all_views` viene eseguito più volte con un tempo > 1 secondo (ad esempio, sta elaborando qualcosa).

## Causa

Quando l’importazione core di Adobe Commerce viene eseguita (manualmente o da [!DNL cron]), quindi viene eseguito un set di plug-in tra più moduli core per determinare quali indici devono essere invalidati.

Il problema si verifica quando **[!UICONTROL Category Permissions]** è abilitato in [!DNL Commerce Admin]. Se questo è vero, allora il plug-in del modulo invalida sempre gli indici di prodotto e categoria (e gli indici collegati) quando viene eseguita un’importazione. Se vengono esaminati i tipi di importazione standard, tutti influiscono **[!UICONTROL Category Permissions]**. È previsto l’annullamento della validità.

Inoltre, quando un sito ha moduli B2B abilitati, se **[!UICONTROL Shared Catalog]** è attivato, si accende e si blocca **[!UICONTROL Category Permissions]**. Spegnimento **[!UICONTROL Shared Catalog]** si sbloccherà **[!UICONTROL Category Permissions]**, ma non spegnerlo.

<u>Controllo [!DNL cron] accedi a [!DNL MySQL] database</u>:

Se accedi a [!DNL MySQL] , possono controllare il tuo `cron` registro per **[!DNL reindex all indexes]** processo.
Questo **dovrebbe** appaiono molte volte, ma il fattore importante è che il processo fa una delle due cose possibili.

Il processo può eseguire solo una di queste due operazioni:

1. Niente: ci vorrebbe da 0 a 1 secondo (un secondo o meno) - il processo controlla per vedere se deve fare qualcosa e poi si interrompe se non ha bisogno di fare nulla.
1. [!DNL Reindex] tutto: ci vorrà sempre del tempo - di solito minuti.

Normalmente si desidera visualizzare molte occorrenze del processo, ma con un tempo di esecuzione inferiore a 1 secondo.
Un commerciante può quindi utilizzare questo [!DNL MySQL] eseguire una query per trovare le transazioni che richiedono **più di 1 secondo** per eseguire:

```sql
SELECT TIMESTAMPDIFF(SECOND, executed_at, finished_at) AS period FROM cron_schedule WHERE job_code = 'indexer_reindex_all_invalid' HAVING period > 1
```

Puoi vedere per quanto tempo viene registrato un periodo eseguendo:

```sql
SELECT executed_at FROM cron_schedule WHERE job_code = 'indexer_reindex_all_invalid' AND executed_at IS NOT NULL ORDER BY executed_at ASC LIMIT 1;
```

Se non si dispone di un periodo di tempo sufficiente per effettuare una valutazione corretta, è possibile aumentare il tempo di un&#39;analisi di successo `cron` il processo viene mantenuto nel registro in seguito a questo [[!DNL Cron] (attività pianificate)](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) e aumentare il **[!DNL Success History Lifetime]** (il valore predefinito è solo 60 minuti).


## Soluzione

Estendi `Magento\CatalogPermissions\Model\Indexer\Plugin\Import` in modo che `afterImportSource` Il metodo esclude l’importazione personalizzata.

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

Dove `ENTITY_CODE` è il valore utilizzato per il parametro del nome dell’entità nel `import.xml` file per l&#39;importazione personalizzata.

## Lettura correlata

[Configura [!DNL cron] lavori](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) nella Guida alla configurazione delle operazioni di Adobe Commerce.
