---
title: Le tabelle MySQL sono troppo grandi
description: Questo articolo illustra il motivo per cui si tratta di un problema quando una tabella MySQL supera 1 GB e come evitarlo.
exl-id: 43f74e3b-7f2e-428c-9964-56d2ce98a34d
feature: Services
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---

# Le tabelle MySQL sono troppo grandi

Questo articolo illustra il motivo per cui si tratta di un problema quando una tabella MySQL supera 1 GB e come evitarlo.

## Prodotti e versioni interessati:

* Adobe Commerce sull’infrastruttura cloud 2.x.x
* Adobe Commerce on-premise 2.x.x

## Problema

La dimensione delle tabelle MySQL non influisce direttamente sulle prestazioni del sito. Tuttavia, se una tabella è di grandi dimensioni, significa che vi sono frequenti operazioni di inserimento su questa tabella, con possibili dati aggiuntivi o dati obsoleti. MySQL è progettato per i database, in cui il rapporto tra operazioni di lettura e scrittura è dell&#39;80%/20%.  Per le tabelle di grandi dimensioni, 1 GB e più, gli indici MySQL, progettati per velocizzare le prestazioni nelle operazioni di lettura, potrebbero compromettere le prestazioni nelle operazioni di scrittura.

## Soluzione

Considera le seguenti opzioni per evitare una diminuzione delle prestazioni:

* Crea un processo CRON per la pulizia di tabelle di grandi dimensioni. Consulta [Trova tabelle MySQL di grandi dimensioni](/help/how-to/general/find-large-mysql-tables.md) nella knowledge base di supporto per consigli su come identificare tabelle di grandi dimensioni.
* Per tabelle di dimensioni superiori a 1 GB, utilizzare un motore MySQL ottimizzato per la scrittura dei registri. Ad esempio, il motore di archiviazione.
* Aggiorna la funzionalità per evitare di archiviare i registri nel database.

## Lettura correlata

[Le tabelle dei log delle modifiche sovradimensionate causano ritardi negli aggiornamenti delle entità](/help/troubleshooting/database/changes-in-the-database-are-not-reflected-on-the-storefront.md) nella nostra knowledge base di supporto.
