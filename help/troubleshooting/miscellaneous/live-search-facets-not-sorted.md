---
title: '[!DNL Live Search] facet non sono in ordine alfabetico'
description: Questo articolo fornisce informazioni sulla risoluzione dei problemi se i facet  [!DNL Live Search]  non sono ordinati alfabeticamente.
feature: Admin Workspace, Categories, Search
role: Developer
source-git-commit: b20a98e44cfad6667b9fe0ab232b0020ed834ca2
workflow-type: tm+mt
source-wordcount: '130'
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
