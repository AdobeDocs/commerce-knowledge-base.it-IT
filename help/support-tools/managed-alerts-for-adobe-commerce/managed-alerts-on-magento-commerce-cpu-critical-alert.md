---
title: "Avvisi gestiti su Adobe Commerce: avviso critico CPU"
description: Questo articolo descrive i passaggi per la risoluzione dei problemi quando si riceve un avviso critico della CPU per Adobe Commerce in New Relic. È necessaria un'azione immediata per risolvere il problema. L’avviso avrà un aspetto simile al seguente, a seconda del canale di notifica dell’avviso selezionato.
exl-id: 45b8ced0-b12f-428b-9838-2a9c26b9874b
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 5be8f2969426078bfcc0e4ffb4895dcf0327165f
workflow-type: tm+mt
source-wordcount: '823'
ht-degree: 0%

---

# Avvisi gestiti su Adobe Commerce: avviso critico CPU

Questo articolo descrive i passaggi per la risoluzione dei problemi quando si riceve un avviso critico della CPU per Adobe Commerce in New Relic. È necessaria un&#39;azione immediata per risolvere il problema. L’avviso avrà un aspetto simile al seguente, a seconda del canale di notifica dell’avviso selezionato.

![avviso disco critico](assets/cpu-critical-magento-managed.png){width="500"}

## Prodotti e versioni interessati

Architettura del piano Pro di Adobe Commerce su infrastruttura cloud

## Problema

In New Relic riceverai un avviso gestito se hai effettuato la registrazione a [Avvisi gestiti per Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) e una o più soglie di avviso sono state superate. Questi avvisi sono stati sviluppati da Adobe Commerce per fornire ai clienti un set standard utilizzando informazioni provenienti da Supporto e Progettazione.

<u>**Esegui!**</u>:

* Interrompi qualsiasi distribuzione pianificata fino a quando l&#39;avviso non viene cancellato.
* Attiva immediatamente la modalità di manutenzione se il sito non risponde o se non risponde completamente. Per i passaggi, consulta [Guida all&#39;installazione > Abilitare o disabilitare la modalità di manutenzione](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) nella documentazione per gli sviluppatori. Assicurarsi di aggiungere l&#39;IP all&#39;elenco degli indirizzi IP esenti per assicurarsi di poter accedere al sito per la risoluzione dei problemi. Per ulteriori informazioni, consulta [Gestire l&#39;elenco degli indirizzi IP esenti](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt) nella documentazione per gli sviluppatori.

<u>**Non fare!**</u>:

* Avvia ulteriori campagne di marketing che possono portare ulteriori visualizzazioni di pagina sul sito.
* Eseguire indicizzatori o nodi aggiuntivi, che possono causare ulteriore stress alla CPU o al disco.
* Esegui le principali attività amministrative (ad esempio, l’amministratore di Commerce, le importazioni/esportazioni di dati).
* Cancella la cache.

Se esegui una delle azioni &quot;Non rispondere&quot; prima di aver indagato e risolto la causa dell’avviso, il sito potrebbe non rispondere (se non stai già verificando un’interruzione).

## Soluzione

Per identificare e risolvere la causa, seguire la procedura riportata di seguito.

>[!WARNING]
>
>Poiché si tratta di un avviso critico, è consigliabile completare il **passaggio 1** prima di provare a risolvere il problema (passaggio 2 in poi).

Controlla se è presente il ticket di supporto Adobe Commerce. Per ulteriori informazioni, consulta [Tracciare i ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) nella Knowledge Base di supporto. Il supporto potrebbe aver ricevuto un avviso di soglia New Relic, aver creato un ticket e iniziato a lavorare sul problema. Se non esiste alcun ticket, creane uno. Il ticket deve contenere le seguenti informazioni:

1. Motivo contatto: selezionare &quot;Avviso New Relic CRITICAL ricevuto&quot;.
1. Descrizione dell&#39;avviso.
1. [Collegamento per incidente New Relic](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Questo è incluso nei tuoi [Avvisi gestiti per Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md).
1. Utilizza la [pagina Transazioni di New Relic APM](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) per identificare le transazioni con problemi di prestazioni:
   * Ordina le transazioni in base ai punteggi di Apdex crescenti. [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) fa riferimento alla soddisfazione degli utenti per il tempo di risposta delle applicazioni e dei servizi Web. Un punteggio Apdex [ basso](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md) può indicare un collo di bottiglia (una transazione con un tempo di risposta più elevato). Di solito, è correlato al database, Redis o PHP. Per i passaggi, fare riferimento a New Relic [Visualizza le transazioni con il più alto livello di insoddisfazione Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * Ordina le transazioni in base alla velocità effettiva più elevata, al tempo medio di risposta più lento, alla quantità di tempo più elevata e ad altre soglie. Per i passaggi, fare riferimento a New Relic [Trova problemi di prestazioni specifici](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems).
1. Se non riesci ancora a identificare l&#39;origine, utilizza la [pagina Infrastruttura di New Relic APM](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page) per identificare i servizi che richiedono molte risorse. Per i passaggi, fare riferimento alla pagina Host di monitoraggio infrastruttura di New Relic [> scheda Processi](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. Se identifichi l’origine, SSH nell’ambiente per approfondire l’analisi. Per ulteriori informazioni, consulta [SSH nell&#39;ambiente per Adobe Commerce sull&#39;infrastruttura cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) nella documentazione per gli sviluppatori.
1. Se hai ancora difficoltà a identificare l’origine:
   * Esamina le tendenze recenti per identificare i problemi relativi alle recenti implementazioni del codice o modifiche alla configurazione (ad esempio, nuovi gruppi di clienti e modifiche di grandi dimensioni al catalogo). È consigliabile verificare negli ultimi sette giorni di attività le correlazioni presenti nelle distribuzioni o nelle modifiche del codice.
   * Valutare la possibilità di verificare e disabilitare i cataloghi flat. Per i passaggi, fare riferimento a [Crons con prestazioni lente e tempi di esecuzione lunghi](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) nella Knowledge Base di supporto.
   * Se sospetti di avere un attacco DDoS, prova a bloccare il traffico da bot. Per i passaggi, consulta [Come bloccare il traffico dannoso per Adobe Commerce sull&#39;infrastruttura cloud al livello Fastly](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) nella nostra knowledge base di supporto.
1. Se il problema sembra temporaneo, esegui passaggi di mitigazione quali un upsize o imposta il sito in modalità di manutenzione. Per ulteriori informazioni, consultare [Come richiedere il ridimensionamento temporaneo](/help/how-to/general/how-to-request-temporary-magento-upsize.md) nella Knowledge Base di supporto e [Guida all&#39;installazione > Abilitare o disabilitare la modalità di manutenzione](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) nella documentazione per gli sviluppatori. Se l’upsize ripristina le normali operazioni del sito, è consigliabile richiedere un upsize permanente (contatta il team dell’account Adobe) o provare a riprodurre il problema nella gestione temporanea dedicata eseguendo un test di carico e ottimizzando le query o il codice che riduce la pressione sui servizi. Per i passaggi, consulta [Distribuzione dei test > Test di carico e stress](https://devdocs.magento.com/cloud/live/stage-prod-test.html#loadtest) nella documentazione per gli sviluppatori per Adobe Commerce sull’infrastruttura cloud.
