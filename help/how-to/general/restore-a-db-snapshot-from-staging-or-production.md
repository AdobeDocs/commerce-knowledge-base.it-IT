---
title: Ripristinare uno snapshot del database da Gestione temporanea o Produzione
description: Questo articolo mostra come ripristinare un’istantanea del database da Staging o Produzione su Adobe Commerce su un’infrastruttura cloud.
exl-id: 1026a1c9-0ca0-4823-8c07-ec4ff532606a
source-git-commit: 193b5118342f380cef925766c0f7956a6592800c
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# Ripristinare uno snapshot del database da [!DNL Staging] o [!DNL Production]

In questo articolo viene illustrato come ripristinare un database [!DNL snapshot] da [!DNL Staging] o [!DNL Production] nell&#39;infrastruttura Adobe Commerce su Cloud Pro.


>[!NOTE]
>
>Questi metodi ripristineranno lo **snapshot completo**.
>&#x200B;>Se è necessario ripristinare lo snapshot **parzialmente**, ad esempio solo ripristinando le tabelle di catalogo senza modificare le tabelle dell&#39;ordine, è necessario consultare lo sviluppatore o il DBA.


## Prodotti e versioni interessati

* Adobe Commerce sull&#39;infrastruttura cloud, [tutte le versioni supportate](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

Scegliere il caso più appropriato:

* [Metodo 1: trasferire il database [!DNL dump] nel computer locale e importarlo](#meth2).
* [Metodo 2: importare il database [!DNL dump] direttamente dal server](#meth3).

## Metodo 1: trasferire il database [!DNL dump] nel computer locale e importarlo {#meth2}


>[!NOTE]
>
> Il formato dello snapshot nei **progetti Azure** sarà diverso e conterrà altri database che **non possono essere importati**.\
> Prima di importare lo snapshot, è necessario eseguire ulteriori passaggi per **estrarre il database appropriato** prima di procedere con l&#39;importazione del dump.

I passaggi sono i seguenti:

1. Utilizzando [!DNL SFTP], passare alla posizione in cui è stato posizionato il database [!DNL snapshot], in genere sul primo server/nodo di [!DNL cluster] (ad esempio: `/mnt/recovery-<recovery_id>`).
   > **Progetti basati su Azure:**\
   > Se il progetto è basato su Azure (ad esempio, l&#39;URL del progetto è `https://us-a1.magento.cloud/projects/<cluster_id>`), l&#39;istantanea verrà inserita in:
   > * `/mnt/shared/<cluster ID>/all-databases.sql.gz`
   > * `/mnt/shared/<cluster ID_stg>/all-databases.sql.gz`

   **Passaggi di estrazione specifici di Azure**

   **Per la produzione:**

   ```bash
   cd /mnt/shared/<cluster ID>/
   gunzip all-databases.sql.gz 
   head -n 17 all-databases.sql > <cluster ID>.sql 
   sed -n '/^-- Current Database: `<cluster ID>`/,/^-- Current Database: `/p' all-databases.sql >> <cluster ID>.sql gzip <cluster ID>.sql
   zcat <cluster ID>.sql.gz | \
   sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | \
   mysql -h 127.0.0.1 \
   -u $DB_USER \
   --password=$MYSQL_PWD $DB_NAME \
   --init-command="SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT ;SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS ;SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION ;SET NAMES utf8 ;SET @OLD_TIME_ZONE=@@TIME_ZONE ;SET TIME_ZONE='+00:00' ;SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 ;SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 ;SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' ;SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0;"
   ```

   **Per Staging:**

   ```bash
   cd /mnt/shared/<cluster ID_stg>/
   gunzip all-databases.sql.gz 
   head -n 17 all-databases.sql > <cluster ID_stg>.sql
   sed -n '/^-- Current Database: `<cluster ID_stg>`/,/^-- Current Database: `/p' all-databases.sql >> <cluster ID_stg>.sql 
   gzip <cluster ID_stg>.sql  
   zcat <cluster ID_stg>.sql.gz | \
   sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | \
   mysql -h 127.0.0.1 \
   -u $DB_USER \
   --password=$MYSQL_PWD $DB_NAME \
   --init-command="SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT ;SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS ;SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION ;SET NAMES utf8 ;SET @OLD_TIME_ZONE=@@TIME_ZONE ;SET TIME_ZONE='+00:00' ;SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 ;SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 ;SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' ;SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0;"
   ```

1. Copiare il database [!DNL dump file] (ad esempio: `<cluster ID>.sql.gz` per [!DNL Production] o `<cluster ID_stg>.sql.gz` per [!DNL Staging]) nel computer locale.
1. Assicurarsi di aver configurato [!DNL SSH tunnel] per la connessione al database in modalità remota: [[!DNL SSH] and [!DNL sFTP]: [!DNL SSH tunneling]](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/secure-connections#env-start-tunn) nella documentazione per gli sviluppatori.
1. Connettersi al database.

   ```bash
   mysql -h <db-host> -P <db-port> -p -u <db-user> <db-name>
   ```

1. [!DNL Drop] il database; al prompt [!DNL MariaDB], immettere:

   (Per [!DNL Production])

   ```bash
   drop database <cluster ID>;
   ```

   (Per [!DNL Staging])

   ```bash
   drop database <cluster ID_stg>;
   ```

1. Immettere il comando seguente per importare [!DNL snapshot]:

   (Per [!DNL Production])

   ```bash
   zcat <cluster ID>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -P <db-port> -p -u   <db-user> <db-name>
   ```

   (Per [!DNL Staging])

   ```bash
   zcat <cluster ID_stg>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -P <db-port> -p -u   <db-user> <db-name>
   ```

## Metodo 2: importare il database [!DNL dump] direttamente dal server {#meth3}

I passaggi sono i seguenti:

1. Passare alla posizione in cui è stato posizionato il database [!DNL snapshot], in genere sul primo server/nodo di [!DNL cluster] (ad esempio: `/mnt/recovery-<recovery_id>`).
1. Per [!DNL drop] e ricreare il database cloud, connettersi innanzitutto al database:

   ```bash
   mysql -h 127.0.0.1 -P <db-port> -p -u <db-user> <db-name>
   ```

1. [!DNL Drop] il database; al prompt [!DNL MariaDB], immettere:

   (Per [!DNL Production])

   ```bash
   drop database <cluster ID>;
   ```

   (Per [!DNL Staging])

   ```bash
   drop database <cluster ID_stg>;
   ```

1. Dopo aver eliminato il database, ricrearlo:

   ```bash
   create database [database_name];
   ```

1. Immettere il comando seguente per importare [!DNL snapshot]:

   (Per importare il backup del database da [!DNL Production])

   ```bash
   zcat <cluster ID>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

   (Per importare il backup del database da [!DNL Staging])

   ```bash
   zcat <cluster ID_stg>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

   (per importare un backup di database da qualsiasi altro ambiente)

   ```bash
   zcat <database-backup-name>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

   (per importare un backup di database da qualsiasi altro ambiente)

   ```bash
   zcat <database-backup-name>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

## Lettura correlata

Nella documentazione per gli sviluppatori:

* [Codice importazione: importare il database](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/deploy/staging-production)
* [[!DNL Snapshots] e [!DNL backup] gestione: [!DNL Dump] database](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/storage/snapshots)
* [Backup (snapshot) nel cloud: domande frequenti](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/faq/backup-snapshot-on-cloud-faq)
