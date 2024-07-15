---
title: L’ordine delle opzioni del bundle non viene aggiornato dall’importazione
description: Questo articolo fornisce una soluzione al problema che si verifica quando, dopo aver importato i prodotti da un file .csv, le opzioni del prodotto bundle appaiono in un ordine diverso da quello in cui sono elencate nel file di importazione.
exl-id: 7f7bf782-4b35-4067-aa94-417097079f1f
feature: Data Import/Export
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 0%

---

# L’ordine delle opzioni del bundle non viene aggiornato dall’importazione

Questo articolo fornisce una soluzione al problema che si verifica quando, dopo aver importato i prodotti da un file .csv, le opzioni del prodotto bundle appaiono in un ordine diverso da quello in cui sono elencate nel file di importazione.

## Prodotti e versioni interessati

* Adobe Commerce sull’infrastruttura cloud 2.2.x, 2.3.x
* Adobe Commerce on-premise 2.2.x, 2.3.x
* Magento Open Source

## Problema

<u>Prerequisiti</u>:

Hai un file .csv valido contenente prodotti bundle.

<u>Passaggi da riprodurre</u>:

1. Importa il file utilizzando la [funzionalità di importazione](https://docs.magento.com/m2/ee/user_guide/system/data-import.html).
1. Apri la pagina del prodotto del bundle.

<u>Risultati previsti</u>:

L&#39;ordine delle opzioni è lo stesso del file .csv.

<u>Risultati effettivi</u>:

L&#39;ordine delle opzioni è diverso da quello nel file .csv.

## Causa

La posizione delle opzioni non è stata dichiarata esplicitamente.

## Soluzione

1. Dichiara esplicitamente una posizione per ogni opzione nel parametro `position` della colonna `bundle_values` nel file .csv. Per istruzioni dettagliate, consulta [Modifica i dati del prodotto](https://docs.magento.com/m2/ee/user_guide/system/data-transfer-bundle-products.html#method-2-edit-the-product-data) nella nostra guida utente.
1. Ripetere l&#39;operazione di importazione.

Per informazioni generali sull&#39;importazione, vedere [Importazione prodotto bundle](https://docs.magento.com/m2/ee/user_guide/system/data-transfer-bundle-products.html) nella guida utente.
