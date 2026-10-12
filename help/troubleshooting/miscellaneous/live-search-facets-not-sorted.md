---
title: '[!DNL Live Search] facet non sono ordinati alfabeticamente'
description: Questo articolo fornisce informazioni sulla risoluzione dei problemi se i facet [!DNL Live Search] non sono ordinati alfabeticamente.
feature: Admin Workspace, Categories, Search
role: Developer
exl-id: 59f86727-c2a6-4418-8753-40f7937e059c
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 0%
---
# [!DNL Live Search] facet non sono ordinati alfabeticamente

## Prodotti e versioni interessati

Adobe Commerce versioni 2.4.x e successive

## Problema

Tutti i facet della vetrina Adobe Commerce sono ordinati alfabeticamente con opzioni di selezione singola, indipendentemente dal tipo di input assegnato all’attributo corrispondente.

## Soluzione alternativa

Tuttavia, in alcuni casi edge, i facet potrebbero non essere ordinati alfabeticamente come impostato nell&#39;[[!DNL Live Search] area di lavoro Faceting](https://experienceleague.adobe.com/it/docs/commerce-merchant-services/live-search/live-search-admin/facets/faceting-workspace).

Come soluzione alternativa, è possibile ordinare gli attributi del prodotto nella sezione degli attributi [!UICONTROL Admin].

1. Nella barra laterale **[!UICONTROL Admin]**, vai a **Archivi** > *Attributi* > **Prodotto**.
1. Selezionare un attributo dalla tabella.

   ![Elenco attributi](assets/attribute-list.png)

1. Apri l&#39;attributo con i valori che desideri ordinare e seleziona **Informazioni attributo** > **Proprietà**.
1. In **Gestisci opzioni** puoi ordinare i valori degli attributi.

   ![Attributi di ordinamento](assets/sort-attributes.png)
