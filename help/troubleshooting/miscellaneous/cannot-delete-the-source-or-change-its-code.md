---
title: Impossibile eliminare l’origine o modificarne il codice
description: Questo articolo corregge alcuni casi in cui non è possibile rimuovere completamente un’origine e/o modificarne il codice.
exl-id: dbdb4d62-9138-4a3d-a58f-8671f1dc5b42
feature: Console
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

Se è necessario rimuovere un&#39;origine dai calcoli di [SSA](https://experienceleague.adobe.com/it/docs/commerce-admin/inventory/basics/selection-reservations) e dall&#39;elaborazione degli ordini di Adobe Commerce Inventory, è possibile disabilitare l&#39;origine. Le origini disattivate conservano tutti i dati, i prodotti assegnati e le quantità di magazzino e possono essere riattivate in qualsiasi momento per ricominciare la spedizione.

Per informazioni dettagliate su come disabilitare un&#39;origine, vedere la [guida alla creazione di origini](https://github.com/magento/inventory/wiki/Create-Sources#disable-sources).
