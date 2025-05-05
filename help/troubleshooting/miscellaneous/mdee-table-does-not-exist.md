---
title: Correggi i dati non aggiornati in [!DNL Commerce Data Exporter] feed e [!DNL cron] registri gli errori con la tabella changelog non esistono
description: Questo articolo fornisce una soluzione per risolvere i problemi di sincronizzazione dei dati causati dall'utilizzo di un ID di visualizzazione errato nella sottoscrizione  [!DNL Commerce Data Exporter mview] .
feature: Data Import/Export, Saas, Logs
role: Developer
exl-id: 50f2223b-bfcf-4c3c-b0f1-dbcc4365edc2
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---

# Correggi i dati non aggiornati nei feed [!DNL Commerce Data Exporter] e [!DNL cron] registra gli errori con la tabella changelog inesistenti

Questo articolo fornisce una soluzione per risolvere i problemi di sincronizzazione dei dati causati dall&#39;utilizzo di un ID di visualizzazione errato nella sottoscrizione [!DNL Data Exporter] [[!DNL Mview]](https://developer.adobe.com/commerce/php/development/components/indexing/#mview). La sottoscrizione [!DNL Mview] viene utilizzata per tenere traccia delle modifiche per le tabelle del database.

## Prodotti e versioni interessati

Istanze di Adobe Commerce in cui il codice personalizzato è stato applicato alla funzionalità di esportazione dei dati (`commerce-data-exporter` o `saas-exporter`). L&#39;errore si verifica se la versione di [[!DNL SaaS] Esportazione dati installata è 103.3.0](https://experienceleague.adobe.com/it/docs/commerce-merchant-services/saas-data-export/release-notes#release-6) o successiva e il codice fa direttamente riferimento all&#39;indice `catalog_data_exporter_products`.

## Problema

I commercianti potrebbero rilevare la mancanza di aggiornamenti dei dati dalle tabelle dei feed [!DNL Data Exporter] del catalogo e visualizzare i seguenti errori nei registri di processo [!DNL cron]:

```
[2024-05-27T19:00:04.627604+00:00] report.ERROR: Cron Job indexer_clean_all_changelogs has an error: Table catalog_data_exporter_products_cl does not exist. Statistics: {"sum":0,"count":1,"realmem":0,"emalloc":0,"realmem_start":305135616,"emalloc_start":283210384} [] [] 
```

## Causa

A causa delle modifiche dei nomi nelle tabelle di feed, negli indici e nelle tabelle di registro delle modifiche nella versione [!DNL Commerce Data Export] [versione 103.3.0](https://experienceleague.adobe.com/it/docs/commerce-merchant-services/saas-data-export/release-notes#release-9), le sottoscrizioni [!DNL Mview] nelle estensioni personalizzate che utilizzano le estensioni [!DNL Commerce Data Export] potrebbero non funzionare correttamente.

In questo caso, l&#39;errore *tabella inesistente* si verifica perché il nome della tabella `catalog_data_exporter` è stato modificato in `cde_products_feed` e si dispone di codice personalizzato che fa riferimento al nome precedente nella sottoscrizione [!DNL Data Exporter Mview].

## Soluzione

Nell&#39;estensione personalizzata, modificare il file di configurazione [!DNL Mview] (```./etc/mview.xml```) per modificare il nome della tabella `catalog_data_exporter_products` in *`cde_products_feed`*.

Nell&#39;esempio seguente viene illustrato il codice che specifica le tabelle tracciate dalla sottoscrizione [!DNL Mview]:

```
<view id="cde_products_feed" class="Magento\CatalogDataExporter\Model\Indexer\ProductFeedIndexer" group="indexer">
     <subscriptions>
         <table name="custom_table" entity_column="product_id" />
     </subscriptions>
</view>
```

## Lettura correlata

* [[!DNL SaaS] Note sulla versione dell&#39;estensione per l&#39;esportazione dei dati](https://experienceleague.adobe.com/it/docs/commerce-merchant-services/saas-data-export/release-notes) nella Guida all&#39;esportazione dei dati di Adobe Commerce per i servizi [!DNL SaaS]
* [Best practice per la modifica delle tabelle del database](https://experienceleague.adobe.com/it/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) nel playbook di implementazione di Commerce
