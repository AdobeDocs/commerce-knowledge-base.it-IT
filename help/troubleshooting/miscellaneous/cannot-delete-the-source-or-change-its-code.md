---
title: Impossibile eliminare l’origine o modificarne il codice
description: Questo articolo corregge alcuni casi in cui non è possibile rimuovere completamente un’origine e/o modificarne il codice.
exl-id: dbdb4d62-9138-4a3d-a58f-8671f1dc5b42
feature: Console
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# Impossibile eliminare l’origine o modificarne il codice

Questo articolo corregge alcuni casi in cui non è possibile rimuovere completamente un’origine e/o modificarne il codice.

## Problema

Le origini non possono essere eliminate indipendentemente dall’assegnazione del prodotto.

## Prodotti e versioni interessati

* Adobe Commerce sull’infrastruttura cloud (tutte le versioni), con inventario Magento installato
* Adobe Commerce on-premise 2.3.0 e versioni successive, con inventario Magento installato
* Magento Open Source 2.3.0 e versioni successive, con Inventario Magenti installato

## Causa

Per progettazione, non è possibile rimuovere completamente un’origine e/o modificarne il codice.

La rimozione completa di un&#39;origine causerebbe problemi di dati dell&#39;ordine perché le origini fanno parte di inventari di prodotti, ordini, dati di spedizione e molto altro.

Il codice è fondamentale per collegare la sorgente agli ordini. Questo è un ID univoco per l’origine e non può essere modificato.

## Soluzione

È possibile rimuovere un&#39;origine da un prodotto trasferendo il magazzino o eliminando il prodotto da tutte le spedizioni in un&#39;ubicazione.

Se devi rimuovere un’origine da [SSA](https://devdocs.magento.com/guides/v2.3/inventory/source-selection-algorithms.html) e l&#39;elaborazione degli ordini di Adobe Commerce Inventory, è possibile disattivare l&#39;origine. Le origini disattivate conservano tutti i dati, i prodotti assegnati e le quantità di magazzino e possono essere riattivate in qualsiasi momento per ricominciare la spedizione.

Consulta la [Guida alla creazione di origini](https://github.com/magento/inventory/wiki/Create-Sources#disable-sources) per informazioni dettagliate su come disattivare un’origine.
