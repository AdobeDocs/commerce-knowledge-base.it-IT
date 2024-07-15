---
title: Stato del magazzino non corretto dopo l’installazione di Inventory management
description: Questo articolo fornisce una correzione per lo stato delle scorte errato dopo l’installazione/aggiornamento di Inventory management.
exl-id: ae32fbe3-deab-4f31-b427-95f8b54a476f
feature: Install, Inventory, Orders
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---

# Stato del magazzino non corretto dopo l’installazione di Inventory management

Questo articolo fornisce una correzione per lo stato delle scorte errato dopo l’installazione/aggiornamento di Inventory management.

## Stato del magazzino non corretto in alcuni siti

Dopo la prima installazione o l’aggiornamento affinché Inventory management si trovi nell’ambiente Adobe Commerce per più siti web, non tutti i siti web dispongono degli stati di stock corretti per i prodotti.

## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud, tutte le versioni, con Inventory management installato
* Adobe Commerce on-premise 2.3.0 e versioni successive, con Inventory management installato
* Magento Open Source 2.3.0 e versioni successive, con Inventory management installato

## Causa

Quando si esegue la prima installazione o aggiornamento, tutti i prodotti vengono assegnati all&#39;origine predefinita, associando tutte le quantità a tale origine. Il Source predefinito viene assegnato al magazzino predefinito, con il sito Web predefinito associato.

## Soluzione

Se disponi di più siti web, devi aggiungerli come Sales Channel al Magazzino predefinito o ad altri titoli personalizzati.

Per informazioni dettagliate su come eseguire questa operazione, consulta la sezione [Stock del wiki/guida utente](https://docs.magento.com/m2/ce/user_guide/catalog/inventory-stock.html) nella guida utente.
