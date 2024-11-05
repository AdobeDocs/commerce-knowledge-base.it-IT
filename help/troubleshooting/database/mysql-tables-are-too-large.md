---
title: '[!DNL MySQL] tabelle sono troppo grandi'
description: In questo articolo viene illustrato il motivo per cui si tratta di un problema quando una tabella  [!DNL MySQL]  supera 1 GB e come evitarlo.
exl-id: 43f74e3b-7f2e-428c-9964-56d2ce98a34d
feature: Services
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# [!DNL MySQL] tabelle sono troppo grandi

In questo articolo viene illustrato perché si tratta di un problema quando una tabella [!DNL MySQL] supera 1 GB e come evitarlo.

## Prodotti e versioni interessati:

* Adobe Commerce sull’infrastruttura cloud 2.x.x
* Adobe Commerce on-premise 2.x.x

## Problema

La dimensione delle tabelle [!DNL MySQL] non influisce direttamente sulle prestazioni del sito. Tuttavia, se una tabella è di grandi dimensioni, significa che vi sono frequenti operazioni di inserimento su questa tabella, con possibili dati aggiuntivi o dati obsoleti. [!DNL MySQL] è progettato per i database, in cui il rapporto tra operazioni di lettura e scrittura è dell&#39;80%/20%.  Per le tabelle di grandi dimensioni, 1 GB e più, gli indici [!DNL MySQL], progettati per velocizzare le prestazioni nelle operazioni di lettura, potrebbero compromettere le prestazioni nelle operazioni di scrittura.

## Soluzione

Considera le seguenti opzioni per evitare una diminuzione delle prestazioni:

* Crea un processo CRON per la pulizia di tabelle di grandi dimensioni. Consulta [Trova [!DNL MySQL] tabelle](/help/how-to/general/find-large-mysql-tables.md) di grandi dimensioni nella Knowledge Base di supporto per suggerimenti su come identificare le tabelle di grandi dimensioni.
* Per tabelle di dimensioni superiori a 1 GB, utilizzare un motore [!DNL MySQL] ottimizzato per la scrittura dei registri. Ad esempio, il motore di archiviazione.
* Aggiorna la funzionalità per evitare di archiviare i registri nel database.

## Lettura correlata

* [Tabelle di log delle modifiche di dimensioni eccessive che causano ritardi negli aggiornamenti delle entità](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/database/changes-in-the-database-are-not-reflected-on-the-storefront) nella Knowledge Base di supporto
* [Best practice per la modifica delle tabelle del database](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) nel playbook di implementazione di Commerce
