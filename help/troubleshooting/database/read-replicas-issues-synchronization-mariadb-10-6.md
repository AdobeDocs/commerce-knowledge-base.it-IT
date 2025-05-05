---
title: Leggi i problemi relativi alle repliche in Adobe Commerce Cloud 2.4.6 con MariaDB 10.6
description: Questo articolo spiega come risolvere i problemi relativi alla lettura delle repliche in Adobe Commerce Cloud 2.4.6 con MariaDB 10.6.
feature: Configuration
role: Developer,Admin
exl-id: b7af1cc3-93ff-40c5-8959-076cedddb56d
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---

# Leggi i problemi relativi alle repliche in Adobe Commerce Cloud 2.4.6 con MariaDB 10.6

Questo articolo fornisce soluzioni per comportamenti imprevisti quando si utilizzano repliche di lettura in Adobe Commerce Cloud 2.4.6 con MariaDB 10.6+.

## Prodotti e versioni interessati

* MariaDB 10.6+
* Adobe Commerce sull’infrastruttura cloud 2.4.6

## Problema

Le letture non critiche mostrano informazioni errate.

## Causa

La configurazione di `slave_parallel_mode` nel database è stata modificata per impostazione predefinita in *optimistic* quando il valore dovrebbe essere *conservative* e il valore `synchronous_replication` in Ece-Tools è impostato per impostazione predefinita su *true* quando il valore dovrebbe essere *false*.

## Soluzione

1. Verificare che il parametro `slave_parallel_mode` sia impostato su *conservativo* (sarà necessario [alzare un ticket di supporto](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket) se il valore non è visualizzato come *conservativo*). Per eseguire il controllo, eseguire il comando seguente:

   ```
    MariaDB [main]> show variables like 'slave_parallel_mode';
    +---------------------+--------------+
    | Variable_name       | Value        |
    +---------------------+--------------+
    | slave_parallel_mode | conservative |
    +---------------------+--------------+
    1 row in set (0.001 sec)
   ```

1. Aggiorna le configurazioni del database `.magento.env.yaml` in:

   ```yaml
       DATABASE_CONFIGURATION:
        _merge: true
           slave_connection:
               default:
                   synchronous_replication: false
   ```



Per i passaggi relativi all&#39;aggiornamento della configurazione del database, fare riferimento a [DATABASE_CONFIGURATION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=it#database_configuration) nell&#39;argomento Distribuisci variabili nella Guida all&#39;infrastruttura di Commerce su Cloud.


## Lettura correlata

* [Configurare le variabili di ambiente per la distribuzione](/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) nella Guida all&#39;infrastruttura di Commerce su Cloud.
* [Best practice per la configurazione del database](/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html) nella playbook di implementazione.
