---
title: Deadlock in MySQL
description: Questo articolo parla dei deadlock in MySQL per aiutarli a identificare e risolvere eventuali problemi di blocco di un sito, blocco dell’importazione del database o altri problemi di Adobe Commerce.
exl-id: 529d1c0b-77f3-4604-9878-e7ea2c9c3640
feature: Best Practices, Services
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# Deadlock in MySQL

Questo articolo parla dei deadlock in MySQL per aiutarli a identificare e risolvere eventuali problemi di blocco di un sito, blocco dell’importazione del database o altri problemi di Adobe Commerce.

## Prodotti e versioni interessati

* Adobe Commerce on-premise 2.2.x e 2.3.x
* Adobe Commerce su infrastruttura cloud 2.2.x e 2.3.x

## Problema

I deadlock in MySQL si verificano quando due o più transazioni si bloccano reciprocamente e richiedono blocchi. I deadlock presenti non sempre indicano un problema, ma spesso sono un sintomo di altri problemi MySQL o Adobe Commerce che si sono verificati.

Spesso i registri dell’applicazione, della distribuzione o MySQL menzionano un *&quot;deadlock&quot;* errore o errore *&quot;Deadlock trovato durante il tentativo di ottenere il blocco. Provare a riavviare la transazione.&quot;*

## Causa

I deadlock possono avere più cause, ma il più comune è l&#39;esecuzione di interazioni (siti web/processi/processi cron/altri utenti/manutenzione MySQL/importazioni MySQL) durante l&#39;esecuzione di query DML/DDL contemporaneamente.

Ad esempio, è consigliabile evitare l&#39;importazione di un database MySQL bloccato attivando prima la modalità di manutenzione per evitare di inviare al database richieste SQL che potrebbero causare deadlock e un&#39;importazione di database bloccata.

## Soluzione

1. Verificare la presenza di errori di deadlock nei registri applicazioni, distribuzione o MySQL:
   * [Posizioni dei registri di Adobe Commerce e Magento Open Source](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/enable-logging.html)
   * [Adobe Commerce sulle posizioni dei registri dell’infrastruttura cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html)
1. Controllare l&#39;elenco dei processi MySQL per l&#39;esecuzione dei processi con il comando `mysql -e 'show full processlist';`
1. Se utilizzi Adobe Commerce su infrastruttura cloud, verifica che MySQL slave sia abilitato. Consulta questo articolo: [Distribuire le variabili (MYSQL\_USE\_SLAVE\_CONNECTION)](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection).
1. A seconda degli errori coinvolti, la soluzione potrebbe presentarsi da sola oppure potrebbe essere necessario includere informazioni di registro utili se è necessario aprire una [Ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

## Lettura correlata

* [Come ridurre al minimo e gestire i deadlock](https://dev.mysql.com/doc/refman/5.7/en/innodb-deadlocks-handling.html)
* [Ottimizzazione indicizzatore - Cambio tabella indicizzatore](https://developer.adobe.com/commerce/php/development/components/indexing/optimization/)
* [Operazioni in blocco - Consumo messaggi](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/)

>[!NOTE]
>
>Siamo consapevoli che questo articolo può ancora contenere termini software standard del settore che alcuni possono trovare razzisti, sessisti o oppressivi e che possono far sentire il lettore ferito, traumatizzato, o sgradito. Adobe sta lavorando per rimuovere questi termini dal nostro codice, dalla nostra documentazione e dalle esperienze utente.
