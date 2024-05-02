---
title: Errori di database relativi a max_allowed_packet su Adobe Commerce
description: Questo articolo fornisce una soluzione per gli errori di connessione al database in "var/log/exception.log" che possono verificarsi quando si importa un numero elevato di prodotti o si esegue un’altra attività che forza il server a gestire pacchetti più grandi di quelli impostati in "max_allowed_packet", che è più grande del valore predefinito, 16 MB.
exl-id: e8932b72-91a3-43ea-800e-a6c7a5a17656
feature: Best Practices, Observability, Services
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# Errori di database relativi a max_allowed_packet su Adobe Commerce

Questo articolo fornisce una soluzione per gli errori di connessione al database in `var/log/exception.log` che possono verificarsi quando si importa un numero elevato di prodotti o si esegue un&#39;altra operazione che impone al server di gestire pacchetti più grandi di quelli impostati in `max_allowed_packet` maggiore del valore predefinito, 16 MB.

## Prodotti e versioni interessati

* Adobe Commerce on-premise [versioni supportate](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problema

Quando un client MySQL o [mysqld](https://dev.mysql.com/doc/refman/8.0/en/mysqld.html) il server riceve un pacchetto maggiore di [max\_allowed\_packet](https://dev.mysql.com/doc/refman/8.0/en/server-system-variables.html#sysvar_max_allowed_packet) byte, emette un [ER\_NET\_PACKET\_TOO\_LARGE](https://dev.mysql.com/doc/mysql-errors/8.0/en/server-error-reference.html#error_er_net_packet_too_large) (che può essere visualizzato nella sezione `exception.log`) e chiude la connessione. Con alcuni clienti, puoi anche ottenere un *Connessione interrotta al server MySQL durante la query* errore se il pacchetto di comunicazione è troppo grande.

<u>Passaggi da riprodurre</u>

Questo problema può essere generato da diverse attività. Ad esempio, puoi tentare di importare un numero elevato di prodotti in Adobe Commerce o eseguire query transazionali per restituire una quantità eccessiva di dati. Il risultato sono errori di connessione al database in `var/log/exception.log` e altri problemi, come la mancata importazione dei prodotti.

## Causa

Il valore predefinito di 16 MB per MySQL `max_allowed_packets` l&#39;impostazione non è abbastanza grande per le tue esigenze.

## Soluzione

1. Identifica le query in cui le singole righe superano la corrente `max_allowed_packet` limite. Tali query devono essere riscritte per ridurre la quantità di dati restituiti. Questo può essere fatto con un numero inferiore di colonne nel `SELECT` o scegliendo un tipo di dati più piccolo per varie colonne come parte della struttura della tabella. Se disponi di un account New Relic, utilizza [Pagina Errori New Relic APM](https://docs.newrelic.com/docs/apm/apm-ui-pages/error-analytics/errors-page-explore-events-behind-errors) e [Pagina Database New Relic APM](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time), e [Registri New Relic](https://docs.newrelic.com/docs/logs/log-management/get-started/get-started-log-management) per cercare le query rilevanti.
1. Per una correzione rapida, puoi richiedere temporaneamente `max_allowed_packet` dimensioni da aumentare quando [invia un ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), ma a discrezione del team di progettazione del cliente, in quanto un valore troppo grande può causare errori di replica causando congestione della rete.
1. Come best practice, è consigliabile eseguire il comando seguente nella CLI per alcune tabelle di database di grandi dimensioni:

   ```
   show table status like [table name to match]
   ```

   Valuta le query in esecuzione su queste tabelle per determinare se stai superando il limite consigliato `max_allowed_packet` 16 MB. Segui lo stesso processo nel passaggio 1 per ridurre i dati restituiti da tali query.

## Lettura correlata

* [Guida all&#39;installazione > MySQL](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/mysql.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=max%20allowed%2016%20MB) nella documentazione per gli sviluppatori.
* [Il caricamento del database perde la connessione a MySQL](/help/troubleshooting/database/database-upload-loses-connection-to-mysql.md) nella nostra knowledge base di supporto.
* [Best practice per il database di Adobe Commerce sull’infrastruttura cloud](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html) nella nostra knowledge base di supporto.
* [Best practice per risolvere i problemi di prestazioni del database](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) nella nostra knowledge base di supporto.
