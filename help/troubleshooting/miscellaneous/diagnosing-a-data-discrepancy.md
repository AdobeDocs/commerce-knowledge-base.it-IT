---
title: Diagnostica di una discrepanza di dati
description: In questo articolo vengono fornite soluzioni per la risoluzione delle discrepanze tra un report di Magento Business Intelligence (MBI) e un report di query o di terze parti.
exl-id: 7d1156cb-9e9b-4426-a0ca-8890b815c245
feature: Commerce Intelligence
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# Diagnostica di una discrepanza di dati

In questo articolo vengono fornite soluzioni per la risoluzione delle discrepanze tra un report di Magento Business Intelligence (MBI) e un report di query o di terze parti.

A seconda della complessità dell’analisi, la generazione del rapporto MBI corrispondente può richiedere una certa familiarità con diversi aspetti della piattaforma. Questo elenco di controllo e i collegamenti correlati ti aiuteranno a comprendere la logica alla base del rapporto, consentendoti di identificare l’origine di eventuali discrepanze.

1. Se un altro membro del team ha creato il rapporto, inizia confermando l’obiettivo e i parametri della loro analisi.
1. Genera punti dati previsti da confrontare con il rapporto MBI in base a una query, uno strumento di reporting di terze parti o una formula.
1. Rivedi e conferma le definizioni di [metric](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/build/reports/ess-manage-data-metrics.html?lang=it) dal collegamento alla metrica nel Report Builder o visitando la scheda [Riepilogo del sistema](https://support.magento.com/hc/en-us/articles/360016730971-Understand-View-definitions-of-metrics-filters-columns-and-column-references-in-the-System-Summary):
   * Tabella dati
   * Operazione
   * Colonna operando, compreso il calcolo se derivato (tramite Riepilogo sistema)
   * Timestamp
   * Per le metriche di abbonamento: date di inizio e fine
   * Filtri, inclusi quelli contenuti in [set di filtri](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/build/reports/ess-manage-data-filters.html?lang=it) applicati
1. Rivedi e conferma altre manipolazioni di dati all’interno del rapporto:
   * Formula calcolata
   * [Raggruppamenti](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html?lang=it#groupby)
   * [Prospettive](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html?lang=it)
   * [Opzioni tempo](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html?lang=it)
   * Per [analisi per coorte](https://support.magento.com/hc/en-us/articles/360016504632-Create-cohort-analysis): data coorte
   * Per [analisi per coorte](https://support.magento.com/hc/en-us/articles/360016504632-Create-cohort-analysis): prospettiva per coorte
1. Se la discrepanza riguarda dati recenti, confermare il punto dati più recente disponibile consultando la sezione **Aggiorna dettagli** nella pagina Connessioni.
1. Se una metrica utilizzata nell&#39;analisi è generata in una tabella del database in cui le righe vengono eliminate da tale tabella, verificare con il team di supporto MBI che la tabella venga controllata per le righe eliminate, nonché la frequenza della ricontrolla e il [metodo di replica](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/best-practices/data/opt-db-analysis.html?lang=it) per la tabella.
1. Allo stesso modo, se le colonne utilizzate nell&#39;analisi possono essere modificate dopo l&#39;aggiunta di una riga, confermare con il supporto che queste colonne vengano [verificate per eventuali modifiche](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/analyze/warehouse-manager/cfg-data-rechecks.html?lang=it), nonché la frequenza della ricontrolla.

**Ancora bloccato?** Non ti preoccupare, siamo qui per aiutarti. Invia una richiesta utilizzando [queste istruzioni](/help/troubleshooting/miscellaneous/mbi-data-discrepancies.md).

## Lettura correlata

[Best practice per la modifica delle tabelle del database](https://experienceleague.adobe.com/it/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) nel playbook di implementazione di Commerce
