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

Questo articolo fornisce una correzione del problema quando non è possibile visualizzare nuovi clienti in **Clienti** > **Tutti i clienti** dopo un&#39;importazione da un file `.csv`. La soluzione consiste nell&#39;impostare l&#39;indicizzatore `customer_grid` sulla modalità &quot;Aggiorna al salvataggio&quot; e reindicizzare manualmente la griglia del cliente.

## Versioni interessate

* Adobe Commerce on-premise 2.2.0 e versioni successive
* Adobe Commerce su infrastruttura cloud 2.2.0 e versioni successive

## Problema

Dopo aver importato nuovi clienti da un file `.csv` utilizzando la funzionalità di importazione nativa di Adobe Commerce, potresti non essere in grado di visualizzare i nuovi record dei clienti in **Clienti** > **Tutti i clienti** nell&#39;amministratore finché non reindicizzi manualmente l&#39;indicizzatore `customer_grid`.

## Causa

La modalità di indicizzazione &quot;Aggiorna secondo pianificazione&quot; in Adobe Commerce 2.2.0 e versioni successive non supporta l&#39;indicizzatore `customer_grid` a causa di problemi di prestazioni.

## Soluzione

Configurare l&#39;indicizzatore `customer_grid` per la reindicizzazione utilizzando la modalità &quot;Aggiorna al salvataggio&quot;. A questo scopo, effettua le seguenti operazioni:

1. Accedi all’amministratore di Commerce.
1. Fare clic su **Sistema** > **Strumenti** > **Gestione indice**.
1. Selezionare la casella di controllo accanto a Indicizzatore griglia cliente.
1. Nell&#39;elenco a discesa **Azioni**, selezionare *Aggiorna al salvataggio*.
1. Fai clic su **Invia**.

È inoltre consigliabile reindicizzare manualmente l&#39;indicizzatore `customer_grid` dopo aver configurato la modalità di indicizzazione per assicurarsi che l&#39;indice sia aggiornato e possa funzionare con cron. Per reindicizzare manualmente, utilizza il seguente comando:

`bin/magento indexer:reindex customer_grid`

## Ulteriori informazioni

Link ad argomenti correlati nella documentazione per gli sviluppatori:

* [Panoramica sull&#39;indicizzazione](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/indexing.html)
* [Gestione degli indicizzatori](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-index.html)
