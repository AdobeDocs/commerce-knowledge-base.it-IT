---
title: La ricerca esatta delle corrispondenze non funziona in Adobe Commerce 2.4.x
description: Questo articolo fornisce un chiarimento per il problema in cui i risultati della ricerca iniziale dell’archivio che utilizzano la stessa stringa di ricerca differiscono in Adobe Commerce 2.4.x rispetto ad Adobe Commerce 2.3.x.
exl-id: 0867558e-1d74-4b83-abf3-651ca7fc32cb
feature: Products, Search
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---

# La ricerca esatta delle corrispondenze non funziona in Adobe Commerce 2.4.x

Questo articolo fornisce un chiarimento per il problema in cui i risultati della ricerca iniziale dell’archivio che utilizzano la stessa stringa di ricerca differiscono in Adobe Commerce 2.4.x rispetto ad Adobe Commerce 2.3.x.

## Prodotti e versioni interessati

- Adobe Commerce (tutti i metodi di distribuzione) 2.4.x, 2.3.x
- Live Search

## Problema

<u>Prerequisiti:</u>

Sono presenti prodotti con valori di attributo `Saga 1` e `Saga 16` negli archivi di Adobe Commerce 2.3 e Adobe Commerce 2.4.

<u>Passaggi da riprodurre:</u>

1. Nella parte anteriore di un negozio basato su Adobe Commerce 2.3, immetti *Saga 1* nel campo di ricerca e fai clic su **Cerca**.
1. Si noti che nei risultati di ricerca si ottengono solo i prodotti con il valore di attributo `Saga 1`.
1. Nella parte anteriore di un negozio basato su Adobe Commerce 2.4, immetti *Saga 1* nel campo di ricerca e fai clic su **Cerca**.

<u>Risultato effettivo:</u>

I risultati della ricerca in 2.4 includono prodotti con valori di attributo `Saga 1` e `Saga 16`.

<u>Risultato previsto:</u>

I risultati della ricerca in 2.4 sono simili a 2.3 e includono solo prodotti con valore di attributo `Saga 1`.

## Causa

La funzionalità di ricerca nativa di Adobe Commerce utilizzata nella versione 2.3.x fornisce risultati di ricerca della corrispondenza esatti. Mentre Live Search, un modulo opzionale disponibile per l’installazione, rilasciato con Adobe Commerce 2.4.x, viene implementato in modo diverso e il risultato effettivo è il comportamento previsto quando il modulo viene utilizzato.

## Lettura correlata

[Installa Live Search](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html) nella guida utente.

[Live Search](https://devdocs.magento.com/live-search/overview.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=Live%20Search) nella documentazione per gli sviluppatori.
