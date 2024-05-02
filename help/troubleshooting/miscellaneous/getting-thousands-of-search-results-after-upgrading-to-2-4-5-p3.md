---
title: Ottenere migliaia di risultati quando si cerca un particolare prodotto
description: Questo articolo fornisce una soluzione al problema che consente di ottenere migliaia di risultati di ricerca quando si cerca un particolare prodotto.
feature: Quotes, Search, Returns
role: Developer, Admin
exl-id: 0eccf212-96be-4ea5-9e6e-95f27d7d9f92
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# Ottenere migliaia di risultati quando si cerca un particolare prodotto

Questo articolo fornisce una soluzione al problema che comporta la visualizzazione di migliaia di risultati di ricerca quando si cerca un prodotto specifico.

## Prodotti e versioni interessati

* Adobe Commerce tutte le versioni con [!DNL ElasticSearch] installato

## Problemi

Stai cercando un prodotto particolare (ad esempio, *WSH12-32-rosso*) ma la ricerca restituisce molti prodotti simili.

## Soluzioni

Natura di una ricerca full-text in [!DNL ElasticSearch] si basa sulla rilevanza, non sulla corrispondenza esatta. Pertanto, le corrispondenze più rilevanti (come lo SKU corrispondente esatto) vengono ordinate per prime.

Tuttavia, se è necessario un risultato di ricerca che corrisponda esattamente al termine di ricerca (corrispondenza esatta), è necessario utilizzare le virgolette per la query di ricerca. Ad esempio, query per *WSH12-32-rosso* senza virgolette restituirà diversi risultati con la corrispondenza esatta (prodotto con *SKU WSH12-32-rosso*) visualizzato per primo nel risultato. Query citata *&quot;WSH12-32-Rosso&quot;* restituirà un solo risultato di corrispondenza esatto.
