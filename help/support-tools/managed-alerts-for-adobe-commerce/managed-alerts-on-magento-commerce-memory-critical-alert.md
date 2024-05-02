---
title: "Avvisi gestiti su Adobe Commerce: avviso di memoria critica"
description: Questo articolo fornisce i passaggi per la risoluzione dei problemi quando si riceve un avviso di memoria critica per Adobe Commerce in New Relic. È necessaria un'azione immediata per risolvere il problema. L’avviso avrà un aspetto simile al seguente, a seconda del canale di notifica dell’avviso selezionato.
exl-id: feed7998-c50b-4cbf-a92d-cbfc65745a1c
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 468ad1c47da3c299b8028726e79e25a4aa9489ea
workflow-type: tm+mt
source-wordcount: '961'
ht-degree: 0%

---

# Avvisi gestiti su Adobe Commerce: avvisi critici per la memoria

Questo articolo fornisce i passaggi per la risoluzione dei problemi quando si riceve un avviso di memoria critica per Adobe Commerce in New Relic. È necessaria un&#39;azione immediata per risolvere il problema. L’avviso avrà un aspetto simile al seguente, a seconda del canale di notifica dell’avviso selezionato.

![avviso critico del disco](assets/memory-critical-magento-managed.png){width="500"}

## Prodotti e versioni interessati

Tutte le versioni di Adobe Commerce su infrastruttura cloud Architettura del piano Pro.

## Problema

Riceverai un avviso gestito in New Relic se ti sei registrato a [Avvisi gestiti per Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) e una o più soglie di allarme sono state superate. Questi avvisi sono stati sviluppati da Adobe per fornire ai clienti un set standard utilizzando le informazioni provenienti da Supporto e Progettazione.

<u> **Sì!** </u>

* Interrompi qualsiasi distribuzione pianificata fino alla cancellazione dell&#39;avviso
* Attiva immediatamente la modalità di manutenzione se il sito non risponde o se non risponde completamente. Per i passaggi, consulta [Guida all’installazione > Abilitare o disabilitare la modalità di manutenzione](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) nella documentazione per gli sviluppatori. Assicurarsi di aggiungere l&#39;IP all&#39;elenco degli indirizzi IP esenti per assicurarsi di poter accedere al sito per la risoluzione dei problemi. Per i passaggi, consulta [Gestisci l&#39;elenco di indirizzi IP esenti](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt) nella documentazione per gli sviluppatori.

<u>**Non farlo!**</u>

* Avvia ulteriori campagne di marketing che possono portare ulteriori visualizzazioni di pagina sul sito.
* Eseguire indicizzatori o nodi aggiuntivi che possono causare ulteriore stress alla CPU o al disco.
* Esegui le principali attività amministrative (ad esempio, amministrazione di Commerce, importazioni/esportazioni di dati).
* Cancella la cache.

Il sito potrebbe non rispondere (se non si è già verificata un’interruzione) se si esegue una delle azioni &quot;Non rispondere&quot; prima di aver indagato e risolto la causa dell’avviso.

## Soluzione

Per identificare e risolvere la causa, seguire la procedura riportata di seguito.

>[!WARNING]
>
>Poiché si tratta di un avviso critico, si consiglia vivamente di completare **Passaggio 1** prima di provare a risolvere il problema (passaggio 2 in poi).

1. Controlla se è presente un ticket di supporto Adobe Commerce. Per i passaggi, consulta [Tracciare i ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) nella nostra knowledge base di supporto. Il supporto potrebbe aver già ricevuto un avviso di soglia New Relic, creato un ticket e iniziato a lavorare sul problema. Se non esiste alcun ticket, creane uno. Il ticket deve contenere le seguenti informazioni:
   * Motivo contatto: selezionare &quot;Avviso New Relic CRITICAL ricevuto&quot;
   * Descrizione della segnalazione
   * [Collegamento per incidente New Relic](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Questo è incluso nel tuo [Avvisi gestiti per Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md).

1. Utilizzare [Pagina Infrastruttura di New Relic APM](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) identificare i processi più impegnativi in termini di memoria. Per i passaggi, consulta New Relic [Monitoraggio dell&#39;infrastruttura: pagina Host > scheda Processi](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes):
   * Se servizi come Redis, MySQL o PHP sono le fonti principali di consumo di memoria, provare a effettuare le seguenti operazioni:
1. Verifica di utilizzare le versioni più recenti. Le versioni più recenti possono a volte correggere le perdite di memoria. Se non utilizzi la versione più recente, puoi procedere con l’aggiornamento. Per i passaggi, consulta [Adobe Commerce su infrastruttura cloud > Servizi > Cambia servizi](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) nella documentazione per gli sviluppatori.
1. Se il problema con il servizio non è correlato alla versione, provare a eseguire le operazioni seguenti:
1. **MySQL**: verifica la presenza di problemi come query con tempi di esecuzione lunghi, chiavi primarie non definite e indici duplicati. Per i passaggi, consulta [Problemi più comuni relativi al database in Adobe Commerce sull’infrastruttura cloud](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) nella nostra knowledge base di supporto.
1. **Redis**: se Redis è la fonte principale di consumo di memoria, [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
1. **PHP**: se PHP è una fonte primaria di consumo di memoria, controllare i processi in esecuzione eseguendo `ps aufx` in CLI/Terminal. Nell’output del terminale vengono visualizzati i processi e i processi cron attualmente in esecuzione. Controlla l’output per il tempo di esecuzione dei processi. Se c&#39;è un cron con un lungo tempo di esecuzione, il cron può essere appeso. Per i passaggi di risoluzione dei problemi, consulta [Prestazioni lente, esecuzione lenta e cronica prolungata](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) e [Processo Cron bloccato nello stato &quot;in esecuzione&quot;](https://support.magento.com/hc/en-us/articles/360033099451) nella nostra knowledge base di supporto.
1. Se hai ancora difficoltà a identificare la fonte del problema, utilizza [Pagina Transazione di New Relic APM](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) per identificare le transazioni con problemi di prestazioni:
   * Ordina le transazioni in base ai punteggi di Apdex crescenti. [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) si riferisce alla soddisfazione degli utenti in merito al tempo di risposta delle applicazioni e dei servizi web. A [Punteggio Apdex basso](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md) può indicare un collo di bottiglia (una transazione con un tempo di risposta più elevato). Di solito si tratta del database, Redis o PHP. Per i passaggi, consulta New Relic [Visualizza transazioni con insoddisfazione Apdex più elevata](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * Ordina le transazioni in base alla velocità effettiva più elevata, al tempo medio di risposta più lento, al tempo più lungo e ad altre soglie. Per i passaggi, consulta New Relic [Individuazione di problemi di prestazioni specifici](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems). Se il problema persiste, utilizzare la pagina Infrastruttura di New Relic APM.
1. Se non riesci a identificare la causa dell’aumento del consumo di memoria, controlla le tendenze recenti per identificare i problemi relativi alle recenti distribuzioni del codice o alle modifiche alla configurazione (ad esempio, nuovi gruppi di clienti e modifiche di grandi dimensioni al catalogo). È consigliabile verificare gli ultimi 7 giorni di attività per eventuali correlazioni nelle distribuzioni o nelle modifiche del codice.
1. Se i metodi di cui sopra non ti aiutano a trovare la causa e/o la soluzione entro un tempo ragionevole, richiedi un upsize o metti il sito in modalità di manutenzione, se non lo hai già fatto. Per i passaggi, consulta [Come richiedere il ridimensionamento temporaneo](/help/how-to/general/how-to-request-temporary-magento-upsize.md) nella nostra knowledge base di supporto, e [Guida all’installazione > Abilitare o disabilitare la modalità di manutenzione](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) nella documentazione per gli sviluppatori.
1. Se l&#39;upsize ripristina le normali operazioni del sito, è consigliabile richiedere un upsize permanente (contattare il team dell&#39;account Adobe) oppure provare a riprodurre il problema nella gestione temporanea dedicata eseguendo un test di carico e ottimizzando le query o il codice che riduce la pressione sui servizi. Consulta [Adobe Commerce su infrastruttura cloud > Distribuzione dei test > Test di carico e stress](https://devdocs.magento.com/cloud/live/stage-prod-test.html#loadtest) nella documentazione per gli sviluppatori.
