---
title: Prestazioni lente a causa della reindicizzazione completa
description: Questo articolo corregge i problemi di prestazioni dovuti alla reindicizzazione completa (in cui vengono aggiornati i dati nelle tabelle del database correlate all’indicizzazione).
exl-id: 4f20a862-cf54-4196-8a88-101f0c80f8f1
feature: Best Practices
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# Prestazioni lente a causa della reindicizzazione completa

Questo articolo corregge i problemi di prestazioni dovuti alla reindicizzazione completa (in cui vengono aggiornati i dati nelle tabelle del database correlate all’indicizzazione).

## Versioni e prodotti interessati

* Adobe Commerce sull’infrastruttura cloud 2.x.x
* Adobe Commerce on-premise 2.x.x

### Problema

Il flushing costante e la ricostruzione dell’indice sono alcuni dei motivi del degrado delle prestazioni. Inoltre, la reindicizzazione completa costante aggiunge blocchi sulle tabelle rendendo il sito web molto più lento del previsto.

### Causa

Le azioni che possono produrre la reindicizzazione completa sono state eseguite dall’amministratore, tra cui:

* Salvataggio attributo prodotto
* Salvataggio visualizzazione sito Web/store/store
* Configurazione archivio

>[!NOTE]
>
>Queste azioni devono essere eseguite al di fuori dell’orario di lavoro per assicurarsi che non influiscano sulle prestazioni durante l’orario di lavoro.

[Anche le estensioni di terze parti](https://support.magento.com/hc/en-us/articles/360042361152-Best-Practices-for-using-third-party-extensions-in-Magento) possono causare la reindicizzazione completa. La reindicizzazione completa può anche essere eseguita manualmente da CLI. Per verificare se è in corso la reindicizzazione degli indici che potrebbe causare il downgrade delle prestazioni:

1. Eseguire questa query per trovare gli indicizzatori completamente reindicizzati negli ultimi 15 minuti:

   ```
   SELECT * FROM indexer_state WHERE updated > NOW() - INTERVAL 15 MINUTE;
   ```

   Il nome di un indicizzatore nell&#39;output indica che l&#39;indicizzatore è stato reindicizzato almeno una volta negli ultimi 15 minuti.

1. Se ha riscontrato una reindicizzazione completa frequente, esegua le seguenti indagini:
   * Chi potrebbe eseguire questa operazione manualmente da CLI
   * Quale modulo di terze parti esegue la reindicizzazione
   * Quale modulo di terze parti contrassegna gli indicizzatori come *Non valido*

### Soluzione

Esegui la reindicizzazione solo quando necessario. Per i passaggi, consulta [Configurare gli indicizzatori](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/manage-indexers#configure-indexers) nella documentazione per gli sviluppatori. Una raccomandazione generale e una best practice è quella di consentire al meccanismo di reindicizzazione parziale di occuparsi della reindicizzazione dei dati senza che sia necessaria alcuna azione manuale da parte di un commerciante. Tutte le reindicizzazioni devono essere eseguite utilizzando la funzionalità nativa di Adobe Commerce (Mview). Mview esegue la reindicizzazione parziale, che è il modo più efficiente per reindicizzare i dati. Per informazioni su Mview, consulta [Panoramica sull&#39;indicizzazione: Mview](https://developer.adobe.com/commerce/php/development/components/indexing/#mview) nella documentazione per gli sviluppatori.

## Lettura correlata

* [Panoramica sull&#39;indicizzazione: come reindicizzare](https://developer.adobe.com/commerce/php/development/components/indexing/#how-to-reindex) nella documentazione per gli sviluppatori.
* [La cache invalidata causa il degrado del tempo di risposta](/help/troubleshooting/miscellaneous/invalidated-cache-causes-response-time-degradation.md) nella knowledge base del supporto.
