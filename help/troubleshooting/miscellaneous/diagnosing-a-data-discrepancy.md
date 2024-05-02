---
title: Diagnostica di una discrepanza di dati
description: In questo articolo vengono fornite soluzioni per la risoluzione delle discrepanze tra un report di Magento Business Intelligence (MBI) e un report di query o di terze parti.
exl-id: 7d1156cb-9e9b-4426-a0ca-8890b815c245
feature: Commerce Intelligence
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# Diagnostica di una discrepanza di dati

In questo articolo vengono fornite soluzioni per la risoluzione delle discrepanze tra un report di Magento Business Intelligence (MBI) e un report di query o di terze parti.

A seconda della complessità dell’analisi, la generazione del rapporto MBI corrispondente può richiedere una certa familiarità con diversi aspetti della piattaforma. Questo elenco di controllo e i collegamenti correlati ti aiuteranno a comprendere la logica alla base del rapporto, consentendoti di identificare l’origine di eventuali discrepanze.

1. Se un altro membro del team ha creato il rapporto, inizia confermando l’obiettivo e i parametri della loro analisi.
1. Genera punti dati previsti da confrontare con il rapporto MBI in base a una query, uno strumento di reporting di terze parti o una formula.
1. Rivedi e conferma [metrica](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/build/reports/ess-manage-data-metrics.html) definizioni, dal collegamento della metrica nel Report Builder o visitando il [Riepilogo sistema](https://support.magento.com/hc/en-us/articles/360016730971-Understand-View-definitions-of-metrics-filters-columns-and-column-references-in-the-System-Summary) scheda:
   * Tabella dati
   * Operazione
   * Colonna operando, compreso il calcolo se derivato (tramite Riepilogo sistema)
   * Timestamp
   * Per le metriche di abbonamento: date di inizio e fine
   * Filtri, inclusi quelli contenuti in [set di filtri](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/build/reports/ess-manage-data-filters.html) applicato
1. Rivedi e conferma altre manipolazioni di dati all’interno del rapporto:
   * Formula calcolata
   * [Raggruppamenti](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html#groupby)
   * [Prospettive](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html)
   * [Opzioni di tempo](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html)
   * Per [analisi per coorte](https://support.magento.com/hc/en-us/articles/360016504632-Create-cohort-analysis): data della coorte
   * Per [analisi per coorte](https://support.magento.com/hc/en-us/articles/360016504632-Create-cohort-analysis): Prospettiva per coorte
1. Se la discrepanza riguarda dati recenti, conferma l’ultimo punto dati disponibile consultando il **Dettagli aggiornamento** nella pagina Connessioni.
1. Se una metrica utilizzata nell&#39;analisi è basata su una tabella del database in cui le righe vengono eliminate, verificare con il team di supporto MBI che la tabella venga controllata per le righe eliminate, nonché la frequenza della verifica e [metodo di replica](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/best-practices/data/opt-db-analysis.html) per il tavolo.
1. Allo stesso modo, se le colonne utilizzate nell’analisi possono essere modificate dopo l’aggiunta di una riga, verifica con supporto che tali colonne siano [ha verificato la presenza di modifiche](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/analyze/warehouse-manager/cfg-data-rechecks.html), nonché la frequenza della nuova verifica.

**Sei ancora inciampato?** Non preoccuparti, siamo qui per aiutarti. Inviaci una richiesta tramite [queste istruzioni](/help/troubleshooting/miscellaneous/mbi-data-discrepancies.md).
