---
title: Errori di database relativi a max_allowed_packet su Adobe Commerce
description: Questo articolo fornisce una soluzione per gli errori di connessione al database in "var/log/exception.log" che possono verificarsi quando si importa un numero elevato di prodotti o si esegue un’altra attività che forza il server a gestire pacchetti più grandi di quelli impostati in "max_allowed_packet", che è più grande del valore predefinito, 16 MB.
exl-id: e8932b72-91a3-43ea-800e-a6c7a5a17656
feature: Best Practices, Observability, Services
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# Errori di database relativi a max_allowed_packet su Adobe Commerce

Questo articolo fornisce una soluzione per gli errori di connessione al database in `var/log/exception.log` che possono verificarsi quando si importa un numero elevato di prodotti o si esegue un&#39;altra attività che costringe il server a gestire pacchetti di dimensioni maggiori di quelle impostate in `max_allowed_packet` e di dimensioni maggiori di quelle predefinite, ovvero 16 MB.

## Prodotti e versioni interessati

* Adobe Commerce on-premise, tutte le [versioni supportate](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problema

Quando un client [!DNL MySQL] o il server [mysqld](https://dev.mysql.com/doc/refman/8.0/en/mysqld.html) riceve un pacchetto maggiore di [max\_allowed\_packet](https://dev.mysql.com/doc/refman/8.0/en/server-system-variables.html#sysvar_max_allowed_packet) byte, viene generato un errore [ER\_NET\_PACKET\_TOO\_LARGE](https://dev.mysql.com/doc/mysql-errors/8.0/en/server-error-reference.html#error_er_net_packet_too_large) (visibile in `exception.log`) e la connessione viene chiusa. Con alcuni client, è inoltre possibile che si ottenga una connessione *interrotta al server [!DNL MySQL] durante l&#39;errore di query* se il pacchetto di comunicazione è troppo grande.

<u>Passaggi da riprodurre</u>

Questo problema può essere generato da diverse attività. Ad esempio, puoi tentare di importare un numero elevato di prodotti in Adobe Commerce o eseguire query transazionali per restituire una quantità eccessiva di dati. Il risultato sono errori di connessione al database in `var/log/exception.log` e altri problemi, come l&#39;importazione dei prodotti non riuscita.

## Causa

Il valore predefinito di 16 MB per l&#39;impostazione [!DNL MySQL] `max_allowed_packets` non è sufficientemente grande per le tue esigenze.

## Soluzione

1. Identifica le query in cui le singole righe superano il limite `max_allowed_packet` corrente. Tali query devono essere riscritte per ridurre la quantità di dati restituiti. Per eseguire l&#39;operazione, è possibile ridurre il numero di colonne nell&#39;istruzione `SELECT` oppure scegliere un tipo di dati più piccolo per varie colonne come parte della struttura della tabella. Se si dispone di un account New Relic, utilizzare la [pagina Errori APM di New Relic](https://docs.newrelic.com/docs/apm/apm-ui-pages/error-analytics/errors-page-explore-events-behind-errors) e la [pagina Database APM di New Relic](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time) e i [registri New Relic](https://docs.newrelic.com/docs/logs/log-management/get-started/get-started-log-management) per cercare le query rilevanti.
1. Per una correzione rapida, è possibile richiedere temporaneamente un aumento delle dimensioni di `max_allowed_packet` quando si [invia un ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), a discrezione del team di progettazione clienti, poiché un valore troppo grande può causare errori di replica causando congestione della rete.
1. Come best practice, è consigliabile eseguire il comando seguente nella CLI per alcune tabelle di database di grandi dimensioni:

   ```
   show table status like [table name to match]
   ```

   Valutare le query in esecuzione su queste tabelle per determinare se si supera la dimensione `max_allowed_packet` consigliata di 16 MB. Segui lo stesso processo nel passaggio 1 per ridurre i dati restituiti da tali query.

## Lettura correlata

* [Panoramica sull&#39;installazione locale](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/overview) nella documentazione per gli sviluppatori.
* [Il caricamento del database perde la connessione a  [!DNL MySQL]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/database/database-upload-loses-connection-to-mysql) nella Knowledge Base di supporto.
* [Best practice per il database di Adobe Commerce sull&#39;infrastruttura cloud](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html) nella knowledge base di supporto.
* [Best practice per risolvere i problemi di prestazioni del database](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) nella knowledge base di supporto.
* [Best practice per la modifica delle tabelle del database](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) nel playbook di implementazione di Commerce
