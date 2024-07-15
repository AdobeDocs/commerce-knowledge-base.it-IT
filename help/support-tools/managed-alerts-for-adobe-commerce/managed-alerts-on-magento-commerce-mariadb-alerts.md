---
title: "Avvisi gestiti su Adobe Commerce: avvisi MariaDB"
description: "In questo articolo vengono illustrati i passaggi per la risoluzione dei problemi quando si ricevono gli avvisi MariaDB per Adobe Commerce in New Relic. Gli avvisi MariaDB monitorano il caricamento elevato delle query e le query DML (Data Manipulation Language) eccessive. Entrambe possono comportare una riduzione dell’esperienza utente o addirittura tempi di inattività. Puoi ricevere quattro tipi di avvisi:"
exl-id: 707e20e0-faba-4bcd-884c-b54568787442
feature: Cache, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---

# Avvisi gestiti su Adobe Commerce: avvisi MariaDB

Questo articolo fornisce i passaggi per la risoluzione dei problemi quando si ricevono gli avvisi MariaDB per Adobe Commerce in New Relic. Gli avvisi MariaDB monitorano il caricamento elevato delle query e le query DML (Data Manipulation Language) eccessive. Entrambe possono comportare una riduzione dell’esperienza utente o addirittura tempi di inattività. Puoi ricevere quattro tipi di avvisi:

* Avviso query DML
* Query DML critiche

## **Prodotti e versioni interessati**

Architettura del piano Pro di Adobe Commerce su infrastruttura cloud

## Problema

In New Relic riceverai un avviso gestito se hai effettuato la registrazione a [Avvisi gestiti per Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) e una o più soglie di avviso sono state superate. Questi avvisi sono stati sviluppati da Adobe per fornire ai clienti un set standard utilizzando le informazioni provenienti da Supporto e Progettazione.

**Esegui!**

* Interrompi qualsiasi distribuzione pianificata fino a quando l&#39;avviso non viene cancellato.
* Attiva immediatamente la modalità di manutenzione se il sito non risponde o se non risponde completamente. Per i passaggi, fare riferimento alla [Guida all&#39;installazione > Abilitare o disabilitare la modalità di manutenzione](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) nella documentazione per gli sviluppatori. Assicurarsi di aggiungere l&#39;IP all&#39;elenco degli indirizzi IP esenti per assicurarsi di poter accedere al sito per la risoluzione dei problemi. Per ulteriori informazioni, vedere [Gestire l&#39;elenco degli indirizzi IP esenti](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt).
* Termina gli script, ad esempio le importazioni, che potrebbero essere la causa dell’avviso se le prestazioni del sito sono interessate.

**Non fare!**

* Eseguire indicizzatori o nodi aggiuntivi che possono causare ulteriore stress su MariaDB.
* Esegui le principali attività amministrative (ad esempio, amministrazione di Commerce, importazioni/esportazioni di dati).
* Cancella la cache.

## Soluzione

**Query DML (query che modificano il database utilizzando UPDATE, INSERT e DELETE)**

Se si riceve un avviso Critico query DML, iniziare dal primo passaggio. Se viene visualizzato un avviso di avviso di query DML, iniziare dal passaggio 2.

1. Controlla se è presente un ticket di supporto Adobe Commerce. Per ulteriori informazioni, consulta la nostra knowledge base [Tracciare i ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets). Il supporto potrebbe aver ricevuto un avviso di soglia New Relic, aver creato un ticket e iniziato a lavorare sul problema. Se non esiste alcun ticket, creane uno. Il ticket deve contenere le seguenti informazioni:
1. Motivo contatto: selezionare &quot;Avviso New Relic MariaDB ricevuto&quot;.
1. Descrizione dell&#39;avviso.
1. [Collegamento per incidente New Relic](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Questo è incluso nei tuoi [Avvisi gestiti per Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md).
1. Per identificare l’origine del problema, prova a identificare le query DML:
1. Rivedi le operazioni del database utilizzando i passaggi della pagina [Pagine interfaccia utente APM di New Relic > Monitoraggio > Database](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time) .
1. Ordina per CONTEGGIO CHIAMATE, quindi OPERAZIONE. Esaminare le operazioni INSERT, DELETE e UPDATE.
1. Cerca AVG alta.
1. Fare clic per trovare i chiamanti delle operazioni del database. In questo modo verranno identificate le transazioni che utilizzano tale query in base al tempo.
1. Cerca ottimizzazioni del codice o ottimizzazioni operative:
1. Ottimizzazioni del codice: cerca di ottimizzare le query con inserimenti/aggiornamenti in blocco, riducendo al minimo l’utilizzo dell’indice o limitando il codice.
1. Ottimizzazioni operative: consente di effettuare l’offload delle modifiche dei dati che richiedono un utilizzo intensivo delle risorse per ridurre i tempi di traffico.
1. Ulteriori ottimizzazioni: accertati di aver utilizzato l’ultima versione di ECE-Tools. Per i passaggi, consulta [Cloud for Adobe Commerce > Update ece-tools version](https://devdocs.magento.com/cloud/project/ece-tools-update.html) nella nostra documentazione per sviluppatori.

## Lettura correlata

* Per ricercare altri problemi comuni relativi a MariaDB, consulta [Problemi più comuni relativi al database per Adobe Commerce sull&#39;infrastruttura cloud](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html).
* Per ricercare le best practice del database, consulta [Best practice del database per Adobe Commerce sull&#39;infrastruttura cloud](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html).
