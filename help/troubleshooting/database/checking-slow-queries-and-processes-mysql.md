---
title: Verifica delle query lente ed elabora MySQL
description: In questo articolo vengono descritti alcuni problemi comuni relativi a MySQL (query lente, processi che richiedono troppo tempo) che possono influire negativamente sul sito di un commerciante e sulle soluzioni indicate.
exl-id: cae02e4f-d8cb-4074-abac-24ead22bdc07
feature: Services
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# Verifica delle query lente ed elabora MySQL

In questo articolo vengono descritti alcuni problemi comuni relativi a MySQL (query lente, processi che richiedono troppo tempo) che possono influire negativamente sul sito di un commerciante e sulle soluzioni indicate.

## Controllo delle &quot;query lente&quot; MySQL

### Descrizione

Se si è verificata un&#39;interruzione potenzialmente causata da un database sovraccarico, questi passaggi consentono di controllare il registro delle query lente del database.

### Analizzare le query utilizzando la riga di comando MySQL (Adobe Commerce Cloud/on-premise/Magento Open Source)

1. Accedi alla riga di comando MySQL (Adobe Commerce on-premise/Magento Open Source) o sul server cloud dalla riga di comando (Adobe Commerce on cloud infrastructure).
1. Esamina il registro delle query lente per le query di durata superiore a 50 secondi:

   ```bash
   grep 'Query_time: [5-9][0-9]\|Query_time: [0-9][0-9][0-9]' /var/log/mysql/mysql-slow.log -A 3
   ```

1. Vai a <https://www.unixtimestamp.com/> (o a un convertitore di marca temporale Unix simile) e inserisci la marca temporale di quando è stata eseguita la query lenta.
1. Se il tempo è correlato a qualsiasi interruzione del sito verificatasi, la causa potrebbe essere un database sovraccarico. Verificare i carichi presenti nel database in quel momento. Esempi di tali carichi potrebbero essere:

* Processi Cron
* Traffico (bot o persone)
* Importa/Esporta script
* Creazione di immagini


### Analizzare le query utilizzando [!DNL Percona Toolkit] (solo Adobe Commerce Pro: architettura cloud)

Se il progetto Adobe Commerce è distribuito su architettura Pro, puoi utilizzare [!DNL Percona Toolkit] per analizzare le query.

1. Eseguire il comando `pt-query-digest --type=slowlog` nei registri query lente MySQL.
   * Per trovare il percorso dei registri di query lente, vedi **[[!UICONTROL Log locations > Service Logs]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html)** nella documentazione per gli sviluppatori.
   * Consulta la documentazione di [[!DNL Percona Toolkit] > pt-query-digest](https://www.percona.com/doc/percona-toolkit/LATEST/pt-query-digest.html#pt-query-digest).
1. In base ai problemi rilevati, puoi adottare le misure necessarie per correggere la query in modo che venga eseguita più rapidamente.

## Controllo dell&#39;&quot;elenco processi&quot; MySQL

### Descrizione

In questo modo sarà possibile stabilire se il server MySQL è attivo e se non sono presenti query bloccate.

### Passaggi

1. Accedi alla riga di comando MySQL (Adobe Commerce on-premise/Magento Open Source) o sul server cloud dalla riga di comando (Adobe Commerce on cloud infrastructure).
1. Accedere a MySQL utilizzando il blocco di codice riportato di seguito. In questo modo verrà automatizzato il processo di accesso.

   ```MySQL
   `export DB_NAME=$(grep [\']db[\'] -A 20 app/etc/env.php | grep dbname | head -n1 | sed "s/.*[=][>][ ]*[']//" | sed "s/['][,]//");    export MYSQL_HOST=$(grep [\']db[\'] -A 20 app/etc/env.php | grep host | head -n1 | sed "s/.*[=][>][ ]*[']//" | sed "s/['][,]//");    export DB_USER=$(grep [\']db[\'] -A 20 app/etc/env.php | grep username | head -n1 | sed "s/.*[=][>][ ]*[']//" | sed "s/['][,]//");    export MYSQL_PWD=$(grep [\']db[\'] -A 20 app/etc/env.php | grep password | head -n1 | sed "s/.*[=][>][ ]*[']//" | sed "s/[']$//" | sed "s/['][,]//");    mysql -h $MYSQL_HOST -u $DB_USER --password=$MYSQL_PWD $DB_NAME -U -A -e 'show processlist;`
   ```

1. Se viene restituito un errore o la risposta richiede più di 30 secondi, contattare il supporto tecnico per controllare il server MySQL.
1. Esaminare l&#39;output di esempio.

1. Ecco alcuni esempi di output:

   ```MySQL
   `$ mysql -h $MYSQL_HOST -u $DB_USER --password=$MYSQL_PWD $DB_NAME -U -A -e 'show processlist;'    +-----------+---------------+--------------------+---------------+---------+------+----------------+------------------------------------------------------------------------------------------------------+----------+    | Id        | User          | Host               | db            | Command | Time | State          | Info                                                                                                 | Progress |    +-----------+---------------+--------------------+---------------+---------+------+----------------+------------------------------------------------------------------------------------------------------+----------+    | 123456789 | abcdefghijklm | 192.168.7.10:12345 | abcdefghijklm | Query   |    0 | Writing to net | SELECT `magento_versionscms_hierarchy_node`.*, `page_table`.`title` AS `page_title`, `page_table`.`i |    0.000 |    | 123456788 | abcdefghijklm | 192.168.7.10:12344 | abcdefghijklm | Sleep   |    0 |                | NULL                                                                                                 |    0.000 |    | 123456777 | abcdefghijklm | 192.168.7.10:12333 | abcdefghijklm | Sleep   |    0 |                | NULL                                                                                                 |    0.000 |    | 123456666 | abcdefghijklm | 192.168.5.8:12222  | abcdefghijklm | Sleep   |    0 |                | NULL                                                                                                 |    0.000 |`
   ```

1. Controllare la colonna &quot;Tempo&quot; per verificare se il tempo è superiore a 1800 secondi; ciò indica che il completamento di un processo richiede potenzialmente troppo tempo. Osservare lo stato dei processi nella colonna &quot;Stato&quot;.
1. Rivedi le query e, se si riscontra che non dovrebbero essere eseguite per un periodo di tempo così lungo, potrebbero terminarle. È possibile che siano previste query con tempi di esecuzione lunghi.


## Lettura correlata

* [Sintassi elenco processi MySQL](https://dev.mysql.com/doc/refman/8.0/en/show-processlist.html) in dev.mysql.com.
* [Sintassi di terminazione MySQL](https://dev.mysql.com/doc/refman/8.0/en/kill.html) in dev.mysql.com.
* [Sicurezza, prestazioni e gestione dati](https://devdocs.magento.com/guides/v2.3/ext-best-practices/extension-coding/security-performance-data-bp.html) nella documentazione per gli sviluppatori.
* [Guida di MySQL](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/mysql.html) nella documentazione per gli sviluppatori.
