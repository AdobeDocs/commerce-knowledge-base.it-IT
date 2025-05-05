---
title: '[!DNL Elasticsearch] viene visualizzato come motore di ricerca nonostante [!DNL OpenSearch] l''installazione'
description: Questo articolo fornisce una soluzione per il problema in cui [!DNL Elasticsearch] viene ancora visualizzato come motore di ricerca per Adobe Commerce sul cloud anche dopo l'installazione o l'aggiornamento a [!DNL OpenSearch].
exl-id: cdd8a35d-da6f-46d3-b732-65626487c9bb
feature: Install
source-git-commit: b3f68e43ce3c4fdea001db1d8ba2774900db7dba
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# [!DNL Elasticsearch] viene visualizzato come motore di ricerca nonostante l&#39;installazione di [!DNL OpenSearch]

Questo articolo fornisce una soluzione per il problema in cui [!DNL Elasticsearch] viene ancora visualizzato come motore di ricerca per Adobe Commerce sul cloud anche dopo l&#39;installazione o l&#39;aggiornamento a [!DNL OpenSearch].

## Versioni interessate

Adobe Commerce su cloud 2.4.4 - 2.4.5-p11

>[!NOTE]
>
>[!DNL OpenSearch] è disponibile come motore di ricerca a partire da Adobe Commerce 2.4.6.

## Problema

[!DNL Elasticsearch] viene ancora visualizzato come motore di ricerca per Adobe Commerce sul cloud anche dopo l&#39;installazione o l&#39;aggiornamento a [!DNL OpenSearch].

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. Controlla il motore di ricerca. Verrà visualizzato [!DNL Elasticsearch7].

## Causa

[!DNL Elasticsearch7] è hardcoded in Adobe Commerce come motore di ricerca utilizzato in queste versioni.

Questo non deve essere confuso con la versione installata del servizio. Anche se nel codice non è incluso un modulo [!DNL Opensearch], Adobe Commerce è in grado di utilizzare il servizio [!DNL Opensearch] sottostante.

## Soluzione

Per verificare se [!DNL OpenSearch] è stato installato, eseguire il comando seguente:

**Metodo 1**:

* Eseguire il comando seguente sul server: `curl 127.0.0.1:9200`. Deve restituire [!DNL OpenSearch] con la relativa versione.

Esempio:

```
$ curl 127.0.0.1:9200
{
  "name" : $clusterName,
  "cluster_name" : "opensearch_stg",
  "cluster_uuid" : $clusterUuid,
  "version" : {
    "distribution" : "opensearch",
    "number" : "1.2.4",
    "build_type" : "deb",
    "build_hash" : "44ccdbaed5fe5a8b02d99a611857a671b6dd909d",
    "build_date" : "2022-11-08T09:23:45.993372Z",
    "build_snapshot" : false,
    "lucene_version" : "8.10.1",
    "minimum_wire_compatibility_version" : "6.8.0",
    "minimum_index_compatibility_version" : "6.0.0-beta1"
  },
  "tagline" : "The OpenSearch Project: https://opensearch.org/"
}
```

**Metodo 2**:

* Utilizzare il comando seguente in Magento-cloud CLI: `magento-cloud relationships -p <project_id>`. Dopo aver utilizzato il comando, individuare [!DNL OpenSearch].

## Lettura correlata

[Configura il servizio OpenSearch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html?lang=it) nella guida Commerce su infrastruttura cloud.
