---
title: Upgrade Compatibility Tool 1.1.0 per Adobe Commerce
description: Upgrade Compatibility Tool 1.1.0 è uno strumento da riga di comando che controlla un’istanza personalizzata di Adobe Commerce rispetto a una versione specifica analizzando tutti i moduli e il codice di base in essa installati. Restituisce un elenco di errori critici, problemi e avvisi che devono essere risolti prima dell’aggiornamento alla versione più recente di Adobe Commerce.
exl-id: 312abc5a-1d6a-4f32-9929-a94f4962eddd
feature: Upgrade
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 0%

---

# Upgrade Compatibility Tool 1.1.0 per Adobe Commerce

Upgrade Compatibility Tool 1.1.0 è uno strumento da riga di comando che controlla un’istanza personalizzata di Adobe Commerce rispetto a una versione specifica analizzando tutti i moduli e il codice di base in essa installati. Restituisce un elenco di errori critici, problemi e avvisi che devono essere risolti prima dell’aggiornamento alla versione più recente di Adobe Commerce.

## Novità di UCT 1.1.0

Upgrade Compatibility Tool 1.1.0 introduce miglioramenti significativi, tra cui:

* **Convalida modifiche file di base**: Adobe consiglia di non personalizzare il codice prodotto di base. Con questa versione, abbiamo aggiunto un punto di controllo per i clienti e i partner per identificare eventuali modifiche al codice di base per comprendere l’impatto delle modifiche in modo rapido e tempestivo. L&#39;aggiunta di questo strumento all&#39;interno del processo di sviluppo consente ai partner e ai commercianti di identificare i problemi in modo proattivo, evitando problemi durante gli aggiornamenti futuri e riducendo il costo totale di proprietà.
* **Esporta il report in un file JSON**: questo miglioramento è stato implementato in seguito al feedback ricevuto dalla community. Ora, quando esegui lo strumento, i dettagli di tutti i problemi identificati vengono esportati in un file JSON, in modo che gli utenti possano leggere, condividere e gestire i risultati senza dover eseguire nuovamente lo strumento.
* **Convalide VBE migliorate**: le VBE (Vendor Bundled Extensions) non fanno parte del codice di base di Adobe Commerce, ma sono testate e supportate da Adobe. Con questo aggiornamento, ora convalidiamo i VBE utilizzando lo stesso approccio utilizzato per il codice di base. Questo miglioramento aiuterà gli utenti a comprendere chiaramente i problemi relativi alle personalizzazioni e ai codici/VBE di base.
* **Fornisci codici di errore**: sono stati introdotti codici di errore per aiutare gli utenti a identificare, comprendere e risolvere i problemi durante un aggiornamento. I messaggi di errore e di avviso forniscono una descrizione chiara e una soluzione suggerita.
* **Possibilità di elencare solo i problemi critici**: con questo, gli utenti potranno concentrarsi solo sui problemi critici e genereranno problemi durante l&#39;aggiornamento.
* **Problemi Delta tra due versioni**: con questo miglioramento proposto dai membri della community, gli utenti UCT saranno in grado di ottenere un delta dei problemi tra due versioni, che consentirà loro di concentrarsi solo sui nuovi problemi introdotti per la versione di destinazione che aggiorneranno.

## Quali versioni può confrontare lo strumento?

Puoi usare lo strumento per confrontare qualsiasi versione 2.x.

## Chi può utilizzare Upgrade Compatibility Tool 1.1.0?

Clienti Adobe Commerce.

## Installare Upgrade Compatibility Tool 1.1.0

Per i passaggi di installazione, consulta Adobe Commerce: [Upgrade Compatibility Tool > Install](https://experienceleague.adobe.com/it/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/run) nella documentazione per gli sviluppatori. Per i prerequisiti per l&#39;utilizzo dello strumento, consulta Adobe Commerce: [Upgrade Compatibility Tool](https://experienceleague.adobe.com/it/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/prerequisites) nella documentazione per gli sviluppatori.

## Qual è il numero accanto a ciascun problema?

Riferimento al messaggio di errore che fornisce informazioni sugli errori che possono verificarsi durante l&#39;esecuzione di Upgrade Compatibility Tool.

I messaggi di errore di Upgrade Compatibility Tool sono suddivisi per livello (problemi critici, errori e avvisi) e per tipo (codice core, codice personalizzato e schemi GraphQL). Ogni tipo contiene le seguenti informazioni:

* Codice di errore: identificatore assegnato da Adobe Commerce al messaggio di errore.
* Descrizione errore: una descrizione che riepiloga la causa dell’errore.
* Azione suggerita per l’errore: se applicabile, fornisce indicazioni per la risoluzione e la risoluzione dell’errore.
* I codici sono elencati e descritti nella [pagina di riferimento del messaggio di errore](https://experienceleague.adobe.com/it/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/reporting/error-messages).

## Dove posso condividere feedback sullo strumento?

Puoi contattare il team UCT nel nostro canale Slack [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F). Saremo lieti di ricevere il tuo feedback e i tuoi suggerimenti per migliorare lo strumento.

## Lettura correlata

* Blog di Adobe Commerce: [Introduzione a Upgrade Compatibility Tool (Alpha)](https://magento.com/blog/magento-news/introducing-upgrade-compatibility-tool)
* Adobe Commerce: [Upgrade Compatibility Tool](https://experienceleague.adobe.com/it/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/overview) nella documentazione per gli sviluppatori.
