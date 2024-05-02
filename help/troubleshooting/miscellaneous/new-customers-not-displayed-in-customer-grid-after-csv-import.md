---
title: I nuovi clienti non vengono visualizzati nella griglia clienti dopo l’importazione CSV
description: Questo articolo fornisce una correzione del problema quando non è possibile visualizzare nuovi clienti in **Clienti** &gt; **Tutti i clienti** dopo un’importazione da un file `.csv`. La soluzione è quella di impostare l’indicizzatore "customer_grid" sulla modalità "Aggiorna al salvataggio" e reindicizzare manualmente la griglia del cliente.
exl-id: e4d9d60a-a0d1-4602-924e-a338e56de61d
feature: Data Import/Export
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# I nuovi clienti non vengono visualizzati nella griglia clienti dopo l’importazione CSV

Questo articolo fornisce una correzione del problema quando non è possibile visualizzare nuovi clienti in **Clienti** > **Tutti i clienti** dopo un’importazione da un `.csv` file. La soluzione è impostare `customer_grid` indicizzatore su &quot;Aggiorna al salvataggio&quot; e reindicizza manualmente la griglia del cliente.

## Versioni interessate

* Adobe Commerce on-premise 2.2.0 e versioni successive
* Adobe Commerce su infrastruttura cloud 2.2.0 e versioni successive

## Problema

Dopo aver importato nuovi clienti da un `.csv` utilizzando la funzionalità di importazione nativa di Adobe Commerce, potrebbe non essere possibile visualizzare i nuovi record cliente in **Clienti** > **Tutti i clienti** in Admin fino a quando non reindicizzi manualmente il `customer_grid` indicizzatore.

## Causa

La modalità di indicizzazione &quot;Aggiorna in base alla pianificazione&quot; in Adobe Commerce 2.2.0 e versioni successive non supporta `customer_grid` indicizzatore per problemi di prestazioni.

## Soluzione

Configurare `customer_grid` indicizzatore da reindicizzare utilizzando la modalità &quot;Aggiorna al salvataggio&quot;. A questo scopo, effettua le seguenti operazioni:

1. Accedi all’amministratore di Commerce.
1. Clic **Sistema** > **Strumenti** > **Gestione indice**.
1. Selezionare la casella di controllo accanto a Indicizzatore griglia cliente.
1. In **Azioni** elenco a discesa, seleziona *Aggiorna al salvataggio*.
1. Clic **Invia**.

Consigliamo inoltre di reindicizzare manualmente `customer_grid` dopo aver configurato la modalità di indicizzazione, verificare che l’indice sia aggiornato e possa funzionare con cron. Per reindicizzare manualmente, utilizza il seguente comando:

`bin/magento indexer:reindex customer_grid`

## Ulteriori informazioni

Link ad argomenti correlati nella documentazione per gli sviluppatori:

* [Panoramica sull’indicizzazione](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/indexing.html)
* [Gestire gli indicizzatori](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-index.html)
