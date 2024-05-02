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

Il `slave_parallel_mode` La configurazione del database è stata modificata per impostazione predefinita in *ottimistica* quando il valore deve essere *conservatore* e `synchronous_replication` valore predefinito in Ece-Tools *true* quando il valore deve essere *false*.

## Soluzione

1. Verifica che la `slave_parallel_mode` il parametro è impostato su *conservatore* (sarà necessario [genera un ticket di supporto](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket) se il valore non viene visualizzato come *conservatore*). Per eseguire il controllo, eseguire il comando seguente:

   ```
    MariaDB [main]> show variables like 'slave_parallel_mode';
    +---------------------+--------------+
    | Variable_name       | Value        |
    +---------------------+--------------+
    | slave_parallel_mode | conservative |
    +---------------------+--------------+
    1 row in set (0.001 sec)
   ```

1. Aggiorna `.magento.env.yaml` configurazioni del database per:

   ```yaml
       DATABASE_CONFIGURATION:
        _merge: true
           slave_connection:
               default:
                   synchronous_replication: false
   ```



Per i passaggi relativi all’aggiornamento della configurazione del database, consulta [DATABASE_CONFIGURATION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#database_configuration) nell’argomento Distribuisci variabili nella Guida di Commerce su Cloud Infrastructure.


## Lettura correlata

* [Configurare le variabili di ambiente per la distribuzione](/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) nella Guida all’infrastruttura cloud di Commerce.
* [Best practice per la configurazione del database](/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html) nel Playbook di implementazione.
