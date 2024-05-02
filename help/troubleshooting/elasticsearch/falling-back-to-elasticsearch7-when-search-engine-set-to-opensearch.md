---
title: Ripristino di [!DNL Elasticsearch7] quando il motore di ricerca è impostato su [!DNL Opensearch]
description: Questo articolo fornisce una soluzione per il problema che si verifica quando un *Fallback to [!DNL Elasticsearch7]* error occurs when the search engine is set to [!DNL OpenSearch] in Adobe Commerce.
feature: Search
role: Developer
exl-id: 965d2929-5cf0-4e0a-9eed-6a656daaa120
source-git-commit: 6b8eecb3df0bb32344a5861a604a40402bb4d392
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 0%

---

# Ripristino di [!DNL Elasticsearch7] quando il motore di ricerca è impostato su [!DNL Opensearch]

Questo articolo fornisce una soluzione al problema quando *Ripristino di[!DNL Elasticsearch7]* si verifica quando il motore di ricerca è impostato su [!DNL OpenSearch] in Adobe Commerce.

## Versioni interessate

Adobe Commerce sull’infrastruttura cloud 2.4.4 - 2.4.5

>[!NOTE]
>
>[!DNL OpenSearch] è disponibile come motore di ricerca a partire da Adobe Commerce 2.4.6.

## Problema

Hai impostato il **motore di ricerca** a **[!DNL OpenSearch]**, ma visualizzare questo tipo di errore nel `var/log/support_report.log` file:

```[2024-04-04T00:27:41.212916+00:00] report.ERROR: opensearch search engine doesn't exist. Falling back to elasticsearch7 [] []```

<u>Passaggi da riprodurre</u>:

1. Verifica che [!DNL OpenSearch] viene installato eseguendo il comando seguente: `curl 127.0.0.1:9200`<br>
Se indica *1.2.4.*, quindi [!DNL OpenSearch] è già installato.
1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. Controlla il motore di ricerca. Verrà visualizzato [!DNL Elasticsearch7].

## Causa

Anche se la tua versione supporta [!DNL OpenSearch], l’applicazione riconoscerà/accetterà solo [!DNL Elasticsearch7] come motore di ricerca.

A partire dalla versione 2.4.6 di Adobe Commerce, l’applicazione è stata aggiornata per consentire [!DNL OpenSearch] da selezionare come motore di ricerca.
Se si passa a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** in un ambiente non cloud, potrai modificare questa opzione come mostrato nella **Soluzione** di seguito.
(Nota: in un ambiente cloud, questo campo non può essere modificato perché il motore di ricerca è bloccato in `app/etc/env.php` file.)

## Soluzione

Aggiornare il `SEARCH_CONFIGURATION` variabile in `.magento.env.yaml` e assicurati che il **motore di ricerca** è impostato su *[!DNL elasticsearch7]*.

## Lettura correlata

[Configura servizio OpenSearch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html) nella guida di Commerce su infrastruttura cloud.
