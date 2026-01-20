---
title: Il server MySQL non è più disponibile​ errore in Adobe Commerce su cloud
description: Questo articolo parla della soluzione al problema per cui ricevi un messaggio di errore " *SQL server has gone away*" nel file "cron.log". Possono verificarsi una serie di sintomi, tra cui problemi di importazione dei file di immagine o errori di distribuzione.
exl-id: 14cb9a6d-6d25-4044-8f52-d65648c03431
feature: Cloud, Paas, Services, Variables
role: Developer
source-git-commit: 5ca7a4400e62db2419b32a31a4f6cf04f5a82e35
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---

# Il server MySQL non è più disponibile&#x200B; errore in Adobe Commerce su cloud

In questo articolo viene illustrata la soluzione del problema per cui viene visualizzato il messaggio di errore &quot; *SQL Server è scomparso*&quot; nel file `cron.log`. Possono verificarsi una serie di sintomi, tra cui problemi di importazione dei file di immagine o errori di distribuzione.

## Prodotti e versioni interessati

* Adobe Commerce sull&#39;infrastruttura cloud, tutte le [versioni supportate](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problema

Viene visualizzato il messaggio di errore &quot; *SQL Server è scomparso*&quot; nel file `cron.log`.

<u>Passaggi da riprodurre</u>

Importare file e attivare una distribuzione.

<u>Risultato previsto</u>

Distribuzione riuscita.

<u>Risultato effettivo</u>

Messaggio di errore in `cron.log` :&quot; *SQLSTATE\[HY000\] \[2006\] Il server MySQL è scomparso at/app/AAAAAAAAA/vendor/magento/zendframework1/library/Zend/Db/Adapter/Pdo/Abstract.php:144&quot;*

## Causa

Il valore `default_socket_timeout` è impostato su un valore troppo basso. La causa è l&#39;impostazione `default_socket_timeout`. Se php non riceve nulla dal database MySQL entro questo periodo, presuppone che sia disconnesso e genera l&#39;errore.

## Soluzione

1. Controllare il periodo di timeout corrente per `default_socket_timeout` eseguendo in CLI:    ```    php -i |grep default_socket_timeout    ```
1. A seconda dell&#39;aumento dell&#39;impostazione di timeout, la variabile `default_socket_timeout` raggiunge il tempo di esecuzione più lungo possibile previsto nel file `/etc/platform/<project_name>/php.ini`. Si consiglia di impostare un valore compreso tra 10 e 15 minuti.
1. Esegui il commit in GIT e ridistribuiscilo.

## Lettura correlata

* [Best practice per il database di Adobe Commerce sull&#39;infrastruttura cloud](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html?lang=it)
* [Problemi di database più comuni in Adobe Commerce sull&#39;infrastruttura cloud](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html?lang=it)
