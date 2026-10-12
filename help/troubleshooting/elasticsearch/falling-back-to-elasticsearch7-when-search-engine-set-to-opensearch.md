---
title: Ripristino di [!DNL Elasticsearch7] quando il motore di ricerca è impostato su [!DNL Opensearch]
description: Questo articolo fornisce una soluzione al problema quando si verifica un errore *Fallback to [!DNL Elasticsearch7]* quando il motore di ricerca è impostato su [!DNL OpenSearch] in Adobe Commerce.
feature: Search
role: Developer
exl-id: 965d2929-5cf0-4e0a-9eed-6a656daaa120
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%
---
# Ripristino di [!DNL Elasticsearch7] quando il motore di ricerca è impostato su [!DNL Opensearch]

Questo articolo fornisce una soluzione al problema quando si verifica un errore *Fallback a[!DNL Elasticsearch7]* quando il motore di ricerca è impostato su [!DNL OpenSearch] in Adobe Commerce.

## Versioni interessate

Adobe Commerce sull’infrastruttura cloud
2.4.4 - 2.4.4-p12
2,4,5 - 2,4,5-p11

>[!NOTE]
>
>[!DNL OpenSearch] è disponibile come motore di ricerca a partire da Adobe Commerce 2.4.6, 2.4.5-p12, 2.4.4-p13.

## Problema

Hai impostato il **motore di ricerca** su **[!DNL OpenSearch]**, ma vedi questo tipo di errore nel file `var/log/support_report.log`:

`[2024-04-04T00:27:41.212916+00:00] report.ERROR: opensearch search engine doesn't exist. Falling back to elasticsearch7 [] []`

<u>Passaggi da riprodurre</u>:

1. Verificare che [!DNL OpenSearch] sia installato eseguendo questo comando: `curl 127.0.0.1:9200`<br>
Se indica *1.2.4*, [!DNL OpenSearch] è già installato.
1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. Controlla il motore di ricerca. Verrà visualizzato [!DNL Elasticsearch7].

## Causa

Anche se la versione in uso supporta [!DNL OpenSearch], l&#39;applicazione riconoscerà/accetterà solo [!DNL Elasticsearch7] come motore di ricerca.

A partire dalla versione 2.4.6 di Adobe Commerce, l&#39;applicazione è stata aggiornata per consentire la selezione di [!DNL OpenSearch] come motore di ricerca.
Se scegli **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** in un ambiente non cloud, potrai modificare questa opzione come mostrato nella **Soluzione** seguente.
(Nota: in un ambiente cloud, questo campo non può essere modificato perché il motore di ricerca è bloccato nel file `app/etc/env.php`).

## Soluzione

Aggiornare la variabile `SEARCH_CONFIGURATION` nel file `.magento.env.yaml` e verificare che il **motore di ricerca** sia impostato su *[!DNL elasticsearch7]*.

## Lettura correlata

[Configura il servizio OpenSearch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html) nella guida Commerce su infrastruttura cloud.
