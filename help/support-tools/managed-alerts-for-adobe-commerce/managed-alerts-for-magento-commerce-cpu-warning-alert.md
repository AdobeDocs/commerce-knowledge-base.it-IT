---
title: 'Avvisi gestiti per Adobe Commerce: avviso CPU'
description: Questo articolo fornisce i passaggi per la risoluzione dei problemi quando si riceve un avviso di avviso della CPU per Adobe Commerce in New Relic. È necessaria un'azione immediata per risolvere il problema. L’avviso avrà un aspetto simile al seguente, a seconda del canale di notifica dell’avviso selezionato.
exl-id: 03686684-3b7e-430a-a05a-a96f38345322
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 0%

---

# Avvisi gestiti per Adobe Commerce: avviso CPU

Questo articolo fornisce i passaggi per la risoluzione dei problemi quando si riceve un avviso di avviso della CPU per Adobe Commerce in New Relic. È necessaria un&#39;azione immediata per risolvere il problema. L’avviso avrà un aspetto simile al seguente, a seconda del canale di notifica dell’avviso selezionato.

![Avviso CPU](assets/cpu-warning-magento-managed.png){width="500"}

## Prodotti e versioni interessati

Architettura del piano Pro di Adobe Commerce su infrastruttura cloud

## Problema

Riceverai un avviso in New Relic se hai firmato fino a [Avvisi gestiti per Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) e una o più soglie di avviso sono state superate. Questi avvisi sono stati sviluppati da Adobe per fornire ai clienti un set standard utilizzando le informazioni provenienti da Supporto e Progettazione.

<u> **Esegui!** </u>

* Interrompi qualsiasi distribuzione pianificata fino a quando l&#39;avviso non viene cancellato.
* Attiva immediatamente la modalità di manutenzione se il sito non risponde completamente. Per i passaggi, consulta [Guida all&#39;installazione > Abilitare o disabilitare la modalità di manutenzione](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) nella documentazione per gli sviluppatori. Assicurarsi di aggiungere l&#39;IP all&#39;elenco degli indirizzi IP esenti per assicurarsi di poter accedere al sito per la risoluzione dei problemi. Per ulteriori informazioni, consulta [Gestire l&#39;elenco degli indirizzi IP esenti](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#instgde-cli-maint-exempt) nella documentazione per gli sviluppatori.

<u>**Non fare!**</u>

* Avvia ulteriori campagne di marketing che possono portare ulteriori visualizzazioni di pagina sul sito.
* Eseguire indicizzatori o nodi aggiuntivi che possono causare ulteriore stress alla CPU o al disco.
* Esegui le principali attività amministrative (ad esempio, amministrazione di Commerce, importazioni/esportazioni di dati).
* Cancella la cache.

## Soluzione

Per identificare e risolvere la causa, seguire la procedura riportata di seguito.

1. Utilizza la [pagina Transazioni di New Relic APM](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) per identificare le transazioni con problemi di prestazioni:
   * Ordina le transazioni in base ai punteggi di Apdex crescenti. [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) fa riferimento alla soddisfazione degli utenti per il tempo di risposta delle applicazioni e dei servizi Web. [Un punteggio Apdex basso](/help/troubleshooting/miscellaneous/troubleshoot-performance-using-new-relic-on-magento-commerce.md#low_user_satisfaction) può indicare un collo di bottiglia (una transazione con un tempo di risposta più elevato). Di solito si tratta del database, Redis o PHP. Per i passaggi, fare riferimento a New Relic [Visualizza le transazioni con il più alto livello di insoddisfazione Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * Ordina le transazioni in base alla velocità effettiva più elevata, al tempo medio di risposta più lento, alla quantità di tempo più elevata e ad altre soglie. Per i passaggi, fare riferimento a New Relic [Trova problemi di prestazioni specifici](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems).
1. Se non riesci ancora a identificare l&#39;origine, utilizza la [pagina Infrastruttura di New Relic APM](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) per identificare i servizi che richiedono molte risorse. Per i passaggi, fare riferimento alla pagina Host di monitoraggio infrastruttura di New Relic [> scheda Processi](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. Se identifichi l’origine, SSH nell’ambiente per approfondire l’analisi. Per ulteriori informazioni, consulta [Cloud for Adobe Commerce > SSH nel tuo ambiente](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections#ssh) nella documentazione per gli sviluppatori.
1. Se hai ancora difficoltà a identificare l’origine:
   * Esamina le tendenze recenti per identificare i problemi relativi alle recenti implementazioni del codice o modifiche alla configurazione (ad esempio, nuovi gruppi di clienti e modifiche di grandi dimensioni al catalogo). È consigliabile verificare negli ultimi sette giorni di attività le correlazioni presenti nelle distribuzioni o nelle modifiche del codice.
   * Valutare la possibilità di verificare e disabilitare i cataloghi flat. Per i passaggi, fare riferimento a [Crons con prestazioni lente e tempi di esecuzione lunghi](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) nella Knowledge Base di supporto.
   * Se sospetti di avere un attacco DDoS, prova a bloccare il traffico da bot. Per i passaggi, consulta [Come bloccare il traffico dannoso per Adobe Commerce al livello Fastly](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) nella nostra knowledge base di supporto.
1. Se il problema sembra temporaneo, esegui passaggi di mitigazione quali un upsize o imposta il sito in modalità di manutenzione. Per ulteriori informazioni, consultare [Come richiedere il ridimensionamento temporaneo](/help/how-to/general/how-to-request-temporary-magento-upsize.md) nella Knowledge Base di supporto e [Guida all&#39;installazione > Abilitare o disabilitare la modalità di manutenzione](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) nella documentazione per gli sviluppatori. Se l’upsize ripristina le normali operazioni del sito, è consigliabile richiedere un upsize permanente (contatta il team dell’account Adobe) o provare a riprodurre il problema nella gestione temporanea dedicata eseguendo un test di carico e ottimizzando le query o il codice che riduce la pressione sui servizi. Per i passaggi, consulta [Cloud for Adobe Commerce > Test Deployment > Load and stress testing](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing) nella documentazione per gli sviluppatori.
