---
title: "Avvisi gestiti per Adobe Commerce: avviso di avvertenza sulla memoria"
description: Questo articolo descrive i passaggi per la risoluzione dei problemi relativi a quando ricevi un avviso di avvertenza sulla memoria per Adobe Commerce in New Relic. È necessaria un'azione immediata per risolvere il problema. L’avviso avrà un aspetto simile al seguente, a seconda del canale di notifica dell’avviso selezionato.
exl-id: bb5eb3f4-b162-4737-93d5-4037f2844bb1
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 8ef51d4e6d6efa51ad4b328a48b84e10c73f3ac6
workflow-type: tm+mt
source-wordcount: '813'
ht-degree: 0%

---

# Avvisi gestiti per Adobe Commerce: avviso di avvertenza memoria

Questo articolo descrive i passaggi per la risoluzione dei problemi relativi a quando ricevi un avviso di avvertenza sulla memoria per Adobe Commerce in New Relic. È necessaria un&#39;azione immediata per risolvere il problema. L’avviso avrà un aspetto simile al seguente, a seconda del canale di notifica dell’avviso selezionato.

![avviso di memoria](assets/memory-warning-magento-managed.png){width="500"}

## Prodotti e versioni interessati

Architettura del piano Pro di Adobe Commerce su infrastruttura cloud

## Problema

Riceverai un avviso in New Relic se ti sei iscritto a [Avvisi gestiti per Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) e una o più soglie di allarme sono state superate. Questi avvisi sono stati sviluppati da Adobe Commerce per fornire ai clienti un set standard utilizzando informazioni provenienti da Supporto e Progettazione.

<u>**Sì!**</u>:

* È consigliabile interrompere qualsiasi distribuzione pianificata fino alla risoluzione dell&#39;avviso.
* Attiva immediatamente la modalità di manutenzione se il sito non risponde o se non risponde completamente. Per i passaggi, consulta [Guida all’installazione > Abilitare o disabilitare la modalità di manutenzione](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) nella documentazione per gli sviluppatori. Assicurarsi di aggiungere l&#39;IP all&#39;elenco degli indirizzi IP esenti per assicurarsi di poter accedere al sito per la risoluzione dei problemi. Per i passaggi, consulta [Gestisci l&#39;elenco di indirizzi IP esenti](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt) nella documentazione per gli sviluppatori.

<u>**Non farlo!**</u>:

* Avvia ulteriori campagne di marketing che possono portare ulteriori visualizzazioni di pagina sul sito.
* Eseguire indicizzatori o nodi aggiuntivi, che possono causare ulteriore stress alla CPU o al disco.
* Esegui le principali attività amministrative (ad esempio, l’amministratore, le importazioni/esportazioni di dati).
* Cancella la cache.

## Soluzione

Per identificare e risolvere la causa, seguire la procedura riportata di seguito.

1. Utilizzare [Pagina Infrastruttura di New Relic APM](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) identificare i processi più impegnativi in termini di memoria. Per i passaggi, consulta New Relic [Monitoraggio dell&#39;infrastruttura: pagina Host > scheda Processi](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes). Se servizi come Redis o MySQL sono la fonte principale di consumo di memoria, provare a effettuare le seguenti operazioni:

   * Verifica di essere nella versione più recente. Le versioni più recenti possono a volte correggere le perdite di memoria. Se non utilizzi la versione più recente, puoi procedere con l’aggiornamento. Per i passaggi, consulta [Adobe Commerce su infrastruttura cloud > Servizi > Cambia servizi](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) nella documentazione per gli sviluppatori.
   * Se non è ancora possibile identificare l&#39;origine di un maggiore consumo di memoria, verificare la presenza di problemi MySQL quali query con esecuzione prolungata, chiavi primarie non definite e indici duplicati. Per i passaggi, consulta [Problemi più comuni relativi al database in Adobe Commerce sull’infrastruttura cloud](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) nella nostra knowledge base di supporto.
   * Se non sono presenti problemi MySQL, verificare la presenza di problemi PHP. Esamina i processi in esecuzione eseguendo `ps aufx` in CLI/Terminal. Nell’output del terminale vengono visualizzati i processi e i processi cron attualmente in esecuzione. Controlla l’output per il tempo di esecuzione dei processi. Se c&#39;è un cron con un lungo tempo di esecuzione, il cron può essere appeso. Fai riferimento a [Prestazioni lente, tempi di esecuzione lenti e lunghi](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) e [Processo Cron bloccato nello stato &quot;in esecuzione&quot;](/help/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.md) nella knowledge base di supporto per la risoluzione dei problemi.

1. Se hai ancora difficoltà a identificare la fonte del problema, utilizza [Pagina Transazione di New Relic APM](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) per identificare le transazioni con problemi di prestazioni:

   * Ordina le transazioni in base ai punteggi di Apdex crescenti. [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) si riferisce alla soddisfazione degli utenti in merito al tempo di risposta delle applicazioni e dei servizi web. A [Punteggio Apdex basso](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md) può indicare un collo di bottiglia (una transazione con un tempo di risposta più elevato). Di solito si tratta del database, Redis o PHP. Per i passaggi, consulta New Relic [Visualizza transazioni con insoddisfazione Apdex più elevata](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * Ordina le transazioni in base alla velocità effettiva più elevata, al tempo medio di risposta più lento, al tempo più lungo e ad altre soglie. Per i passaggi, consulta New Relic [Individuazione di problemi di prestazioni specifici](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems). Se il problema persiste, utilizzare la pagina Infrastruttura di New Relic APM.

1. Se non riesci a identificare la causa dell’aumento del consumo di memoria, controlla le tendenze recenti per identificare i problemi relativi alle recenti distribuzioni del codice o alle modifiche alla configurazione (ad esempio, nuovi gruppi di clienti e modifiche di grandi dimensioni al catalogo). È consigliabile verificare negli ultimi sette giorni di attività le correlazioni presenti nelle distribuzioni o nelle modifiche del codice.

1. Se i metodi di cui sopra non ti aiutano a trovare la causa e/o la soluzione entro un tempo ragionevole, richiedi un upsize o metti il sito in modalità di manutenzione, se non lo hai già fatto. Per i passaggi, consulta [Come richiedere il ridimensionamento temporaneo](/help/how-to/general/how-to-request-temporary-magento-upsize.md) nella nostra knowledge base di supporto e [Guida all’installazione > Abilitare o disabilitare la modalità di manutenzione](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) nella documentazione per gli sviluppatori.

1. Se l&#39;upsize ripristina le normali operazioni del sito, è consigliabile richiedere un upsize permanente (contattare il team dell&#39;account Adobe) oppure provare a riprodurre il problema nella gestione temporanea dedicata eseguendo un test di carico e ottimizzando le query o il codice che riduce la pressione sui servizi. Fai riferimento a [Adobe Commerce su infrastruttura cloud > Distribuzione dei test > Test di carico e stress](https://devdocs.magento.com/cloud/live/stage-prod-test.html#loadtest) nella documentazione per gli sviluppatori.
