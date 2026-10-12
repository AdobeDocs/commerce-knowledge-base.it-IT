---
title: Ottenere migliaia di risultati quando si cerca un particolare prodotto
description: Questo articolo fornisce una soluzione al problema che consente di ottenere migliaia di risultati di ricerca quando si cerca un particolare prodotto.
feature: Quotes, Search, Returns
role: Developer, Admin
exl-id: 0eccf212-96be-4ea5-9e6e-95f27d7d9f92
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 792a7e9b-6519-5e99-a913-56c3dd2408da
    internal-label: Quotes
  - id: ac07462c-732c-5c1c-947b-4ce533b4fcfb
    internal-label: Returns
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 0%
---
# Ottenere migliaia di risultati quando si cerca un particolare prodotto

Questo articolo fornisce una soluzione al problema che comporta la visualizzazione di migliaia di risultati di ricerca quando si cerca un prodotto specifico.

## Prodotti e versioni interessati

* Adobe Commerce tutte le versioni con [!DNL ElasticSearch] installato

## Problemi

Stai cercando un prodotto particolare (ad esempio, *WSH12-32-Red*) ma la ricerca restituisce molti prodotti simili.

## Soluzioni

La natura di una ricerca full-text in [!DNL ElasticSearch] si basa sulla rilevanza, non sulla corrispondenza esatta. Pertanto, le corrispondenze più rilevanti (come lo SKU corrispondente esatto) vengono ordinate per prime.

Tuttavia, se è necessario un risultato di ricerca che corrisponda esattamente al termine di ricerca (corrispondenza esatta), è necessario utilizzare le virgolette per la query di ricerca. Ad esempio, la query per *WSH12-32-Red* senza virgolette restituirà diversi risultati con la corrispondenza esatta (prodotto con *SKU WSH12-32-Red*) visualizzata per prima nel risultato. Ma la query tra virgolette *&quot;WSH12-32-Red&quot;* restituirà solo un risultato di corrispondenza esatto.
