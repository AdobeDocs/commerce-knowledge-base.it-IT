---
title: '''[!DNL Elasticsearch] viene visualizzato come motore di ricerca nonostante [!DNL OpenSearch] installazione"'
description: Questo articolo fornisce una soluzione per il problema in cui [!DNL Elasticsearch] viene ancora visualizzato come motore di ricerca per Adobe Commerce su cloud anche dopo l’installazione o l’aggiornamento a [!DNL OpenSearch].
exl-id: cdd8a35d-da6f-46d3-b732-65626487c9bb
feature: Install
source-git-commit: 1a36e74807e6d32b0810416b6fb61aeca6f9be94
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# [!DNL Elasticsearch] viene visualizzato come motore di ricerca nonostante [!DNL OpenSearch] installazione

Questo articolo fornisce una soluzione per il problema in cui [!DNL Elasticsearch] viene ancora visualizzato come motore di ricerca per Adobe Commerce su cloud anche dopo l’installazione o l’aggiornamento a [!DNL OpenSearch].

## Versioni interessate

Adobe Commerce su cloud 2.4.3-p2 - 2.4.5-p6

>[!NOTE]
>
>[!DNL OpenSearch] è disponibile come motore di ricerca a partire da Adobe Commerce 2.4.6.

## Problema

[!DNL Elasticsearch] viene ancora visualizzato come motore di ricerca per Adobe Commerce su cloud anche dopo l’installazione o l’aggiornamento a [!DNL OpenSearch].

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. Controlla il motore di ricerca. Verrà visualizzato [!DNL Elasticsearch7].

## Causa

Adobe Commerce è hardcoded per specificare [!DNL Elasticsearch7] come motore di ricerca.

## Soluzione

Per verificare se [!DNL OpenSearch] è stato installato, eseguire il comando seguente:

**Metodo 1**:

* Esegui il comando seguente sul server: `curl 127.0.0.1:9200`. Deve restituire [!DNL OpenSearch] con la sua versione.

**Metodo 2**:

* Utilizza il seguente comando sulla CLI del cloud di Magento: `magento-cloud relationships -p <project_id>`. Dopo aver utilizzato il comando, individua [!DNL OpenSearch].

## Lettura correlata

[Configura servizio OpenSearch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html) nella guida di Commerce su infrastruttura cloud.
