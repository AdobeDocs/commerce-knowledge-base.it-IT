---
title: Lo stato dell'indice Elasticsearch è 'giallo' o 'rosso'
description: L’articolo corregge quando lo stato dell’indice Elasticsearch non è "*green*". '*giallo*' indica normale e '*rosso*' indica cattivo. Lo stato "giallo" o "rosso" può comparire insieme a prodotti mancanti o alla visualizzazione di informazioni sul prodotto obsolete.
exl-id: 27689511-6a41-41a9-8dda-a627d2f65263
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# Lo stato dell&#39;indice Elasticsearch è &#39;giallo&#39; o &#39;rosso&#39;

>[!WARNING]
>
> [Il motore di ricerca del catalogo MySQL verrà rimosso in Adobe Commerce 2.4.0](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md). Prima di installare la versione 2.4.0, è necessario aver configurato e configurato l’host Elasticsearch. Consulta [Installare e configurare Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html).

L&#39;articolo fornisce una correzione quando lo stato dell&#39;indice Elasticsearch non è &#39;*green*&#39;. &#39;*giallo*&#39; indica normale e &#39;*rosso*&#39; indica non valido. Lo stato &quot;giallo&quot; o &quot;rosso&quot; può comparire insieme a prodotti mancanti o alla visualizzazione di informazioni sul prodotto obsolete.

## Versioni e prodotti interessati

* Adobe Commerce sull’infrastruttura cloud 2.2.x, 2.3.x
* Adobe Commerce on-premise 2.2.x, 2.3.x

## Problema

L&#39;indice di ricerca del catalogo di Elasticsearch è lento e lo stato risultante è &#39;*giallo*&#39; o &#39;*rosso*&#39; anziché &#39;*verde*&#39;. Potresti anche riscontrare delle modifiche mancanti sul front-end.

## Causa

Le possibili cause possono essere diverse. Una causa è l&#39;esaurimento dello spazio su disco dell&#39;istanza di Elasticsearch. Un&#39;altra causa è la duplicazione degli indici.

## Soluzione

Crea un nuovo dump mysql prima di seguire questi passaggi ed eseguili al di fuori dell’orario di lavoro per evitare di influire potenzialmente sui client:

1. Passa temporaneamente alla ricerca MySQL. Abilitare la ricerca MySQL. (Nota: ricorda di tornare a Elasticsearch o potresti riscontrare problemi di prestazioni).
1. Per identificare gli indici duplicati, eseguire il comando seguente:

   ```
   curl --silent -X GET localhost:9200/_cat/indices?v
   ```

1. Per eliminare gli indici:

   ```
   curl -XDELETE localhost:9200/[your_index_name_here]
   ```

1. Riattiva Elasticsearch.
1. Esegui reindicizzazione completa.
1. Controllare lo stato degli indici eseguendo il comando seguente:

   ```
   curl --silent -X GET localhost:9200/_cat/indices?v
   ```

Se questi passaggi non funzionano, [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

## Lettura correlata

Per ulteriori informazioni, fare riferimento a [Elasticsearch Cluster Health API](https://www.elastic.co/guide/en/elasticsearch/reference/current/cluster-health.html).
