---
title: Ripristinare uno snapshot del database da Gestione temporanea o Produzione
description: Questo articolo mostra come ripristinare un’istantanea del database da Staging o Produzione su Adobe Commerce su un’infrastruttura cloud.
exl-id: 1026a1c9-0ca0-4823-8c07-ec4ff532606a
source-git-commit: b9e72ff8d541ad01788e5198e03abcb46a1bd11f
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# Ripristinare uno snapshot del database da [!DNL Staging] o [!DNL Production]

Questo articolo mostra come ripristinare un database [!DNL snapshot] da [!DNL Staging] o [!DNL Production] su infrastruttura Adobe Commerce on Cloud Pro.

## Prodotti e versioni interessati

* Adobe Commerce sull’infrastruttura cloud, [tutte le versioni supportate](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

Scegliere il caso più appropriato:

* [Metodo 1: trasferire il database [!DNL dump] nel computer locale e importarlo](#meth2).
* [Metodo 2: importare il database [!DNL dump] direttamente dal server](#meth3).

## Metodo 1: trasferire il database [!DNL dump] nel computer locale e importarlo {#meth2}

I passaggi sono i seguenti:

1. Utilizzo di [!DNL sFTP], passare alla posizione in cui il database [!DNL snapshot] è stato posizionato, in genere sul primo server/nodo del [!DNL cluster] Ad esempio: `/mnt/recovery-<recovery_id>`). NOTA: se il progetto è basato su Azure, ad esempio, l’URL del progetto avrà un aspetto simile a https://us-a1.magento.cloud/projects/&lt;cluster_id>, quindi l&#39;istantanea verrà inserita in `/mnt/shared/<cluster ID>/all-databases.sql.gz` o `/mnt/shared/<cluster ID_stg>/all-databases.sql.gz` invece.

   NOTA: il formato dello snapshot nei progetti di Azure sarà diverso e conterrà altri database che non possono essere importati. Prima di importare lo snapshot, è necessario eseguire ulteriori operazioni per estrarre il database appropriato prima di importare il dump.

   Per la produzione:

   ```sql
   cd /mnt/shared/<cluster ID/
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

   Per staging:

   ```sql
   cd /mnt/shared/<cluster ID/ | cd /mnt/shared/<cluster ID_stg>
   gunzip all-databases.sql.gz 
   head -n 17 all-databases.sql > <cluster ID_stg>.sql
   sed -n '/^-- Current Database: `wyf2o4zlrljjs`/,/^-- Current Database: `/p' all-databases.sql >> <cluster ID_stg>.sql 
   gzip <cluster ID_stg>.sql  
   zcat <cluster ID_stg>.sql.gz | \
   sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | \
   mysql -h 127.0.0.1 \
   -u $DB_USER \
   --password=$MYSQL_PWD $DB_NAME \
   --init-command="SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT ;SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS ;SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION ;SET NAMES utf8 ;SET @OLD_TIME_ZONE=@@TIME_ZONE ;SET TIME_ZONE='+00:00' ;SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 ;SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 ;SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' ;SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0;"
   ```

1. Copiare il database [!DNL dump file] Ad esempio: `<cluster ID>.sql.gz` per [!DNL Production] o `<cluster ID_stg>.sql.gz` per [!DNL Staging]) nel computer locale.
1. Assicurati di aver impostato [!DNL SSH tunnel] per connettersi al database in modalità remota: [[!DNL SSH] e [!DNL sFTP]: [!DNL SSH tunneling]](https://devdocs.magento.com/cloud/env/environments-ssh.html#env-start-tunn) nella documentazione per gli sviluppatori.
1. Connettersi al database.

   ```sql
   mysql -h <db-host> -P <db-port> -p -u <db-user> <db-name>
   ```

1. [!DNL Drop] la banca dati; alla [!DNL MariaDB] prompt, immetti:

   (Per [!DNL Production])

   ```sql
   drop database <cluster ID>;
   ```

   (Per [!DNL Staging])

   ```sql
   drop database <cluster ID_stg>;
   ```

1. Immetti il seguente comando per importare [!DNL snapshot]:

   (Per [!DNL Production])

   ```sql
   zcat <cluster ID>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -P <db-port> -p -u   <db-user> <db-name>
   ```

   (Per [!DNL Staging])

   ```sql
   zcat <cluster ID_stg>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -P <db-port> -p -u   <db-user> <db-name>
   ```

## Metodo 2: importare il database [!DNL dump] direttamente dal server {#meth3}

I passaggi sono i seguenti:

1. Passare alla posizione in cui si trova il database [!DNL snapshot] è stato posizionato, in genere sul primo server/nodo del [!DNL cluster] Ad esempio: `/mnt/recovery-<recovery_id>`).
1. A [!DNL drop] e ricreare il database cloud, prima connettiti al database:

   ```sql
   mysql -h 127.0.0.1 -P <db-port> -p -u <db-user> <db-name>
   ```

1. [!DNL Drop] la banca dati; alla [!DNL MariaDB] prompt, immetti:

   (Per [!DNL Production])

   ```sql
   drop database <cluster ID>;
   ```

   (Per [!DNL Staging])

   ```sql
   drop database <cluster ID_stg>;
   ```

1. Immetti il seguente comando per importare [!DNL snapshot]:

   (Per [!DNL Production])

   ```sql
   zcat <cluster ID>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

   (Per [!DNL Staging])

   ```sql
   zcat <cluster ID_stg>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

## Lettura correlata

Nella documentazione per gli sviluppatori:

* [Importa codice: importa il database](https://devdocs.magento.com/cloud/setup/first-time-setup-import-import.html#cloud-import-db)
* [[!DNL Snapshots] e [!DNL backup] gestione: [!DNL Dump] database](https://devdocs.magento.com/cloud/project/project-webint-snap.html#db-dump)
