---
title: Il server MySQL non è più disponibile​ errore in Adobe Commerce su cloud
description: Questo articolo parla della soluzione al problema per cui ricevi un messaggio di errore " *SQL server has gone away*" nel file "cron.log". Possono verificarsi una serie di sintomi, tra cui problemi di importazione dei file di immagine o errori di distribuzione.
exl-id: 14cb9a6d-6d25-4044-8f52-d65648c03431
feature: Cloud, Paas, Services, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# Il server MySQL non è più disponibile&#x200B; errore in Adobe Commerce su cloud

Questo articolo parla della soluzione per il problema in cui si riceve un &quot; *SQL Server non più disponibile* messaggio di errore &quot; in `cron.log` file. Possono verificarsi una serie di sintomi, tra cui problemi di importazione dei file di immagine o errori di distribuzione.

## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud, tutto [versioni supportate](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problema

Ricevi un’&quot; *SQL Server non più disponibile* messaggio di errore &quot; in `cron.log` file.

<u>Passaggi da riprodurre</u>

Importare file e attivare una distribuzione.

<u>Risultato previsto</u>

Distribuzione riuscita.

<u>Risultato effettivo</u>

Messaggio di errore in `cron.log` :&quot; *SQLSTATE\[HY000\] \[2006\] Il server MySQL non è più disponibile at/app/AAAAAAAAA/vendor/magento/zendframework1/library/Zend/Db/Adapter/Pdo/Abstract.php:144&quot;*

## Causa

Il `default_socket_timeout` il valore è impostato su un valore troppo basso. Ciò è causato dall&#39;impostazione `default_socket_timeout` . Se php non riceve nulla dal database MySQL entro questo periodo, presuppone che sia disconnesso e genera l&#39;errore.

## Soluzione

1. Controlla il periodo di timeout corrente per `default_socket_timeout` eseguendo in CLI:    ```    php -i |grep default_socket_timeout    ```
1. A seconda dell&#39;impostazione di timeout, il `default_socket_timeout` variabile al tempo di esecuzione più lungo possibile previsto nel `/etc/platform/<project_name>/php.ini` file. Si consiglia di impostare un valore compreso tra 10 e 15 minuti.
1. Esegui il commit in GIT e ridistribuiscilo.

## Lettura correlata

* [Il caricamento del database perde la connessione a MySQL](/help/troubleshooting/database/database-upload-loses-connection-to-mysql.md)
* [Best practice per il database di Adobe Commerce sull’infrastruttura cloud](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html)
* [Problemi di database più comuni in Adobe Commerce sull’infrastruttura cloud](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html)
