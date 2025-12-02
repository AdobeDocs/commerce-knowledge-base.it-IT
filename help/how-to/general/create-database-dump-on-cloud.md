---
title: Creazione di un dump del database sull’infrastruttura cloud di Adobe Commerce
description: Questo articolo illustra i modi possibili (e consigliati) per creare un’immagine database (DB) su Adobe Commerce nell’infrastruttura cloud.
exl-id: 4a2e54ac-8d65-4e51-8337-08f9748dc6c0
feature: Cloud
source-git-commit: 96b145a1f76c296907da96fd97c7a8f7778463f8
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# Creazione di un dump del database sull’infrastruttura cloud di Adobe Commerce

Questo articolo illustra i modi possibili (e consigliati) per creare un’immagine database (DB) su Adobe Commerce nell’infrastruttura cloud.

Per scaricare il database è sufficiente utilizzare una sola variante (opzione). Queste opzioni si applicano a qualsiasi tipo di ambiente (integrazione, staging, produzione) e a qualsiasi piano (Adobe Commerce su infrastruttura cloud Architettura del piano Starter e Adobe Commerce su infrastruttura cloud Architettura del piano Pro).

## Prerequisito: SSH per l’ambiente

Per eseguire il dump del database sull&#39;infrastruttura cloud di Adobe Commerce con qualsiasi variante descritta in questo articolo, devi prima [SSH nell&#39;ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).

>[!WARNING]
>
>Se si sceglie l&#39;opzione 1 o l&#39;opzione 2, eseguire il comando durante le ore non di punta su un nodo secondario del database.

## Opzione 1: db-dump (**ece-tools; consigliato**)

Puoi scaricare il tuo database utilizzando il comando [ECE-Tools](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html):

```php
vendor/bin/ece-tools db-dump
```

Questa è l’opzione consigliata e più sicura.

Consulta [Eseguire il dump del database (ECE-Tools)](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/database-dump.html) nella Guida all&#39;infrastruttura cloud di Commerce.

## Opzione 2: mariadb-dump (o mysqldump per le versioni precedenti)

+++<b>Per le versioni più recenti di MariaDB (11.x e versioni successive)</b>

A partire da MariaDB 11.0.1, il collegamento simbolico `mysqldump` è diventato obsoleto. Si consiglia di utilizzare `mariadb-dump`.

Per ulteriori informazioni, vedere [utilità client mariadb-dump](https://mariadb.com/docs/server/clients-and-utilities/backup-restore-and-import-clients/mariadb-dump).

+++

+++<b>Per le versioni precedenti di MariaDB</b> 

Se si utilizza una versione precedente di MariaDB in cui `mariadb-dump` non è disponibile, è possibile scaricare il database utilizzando il comando nativo MySQL `mysqldump`.

>[!WARNING]
>
>Non eseguire questo comando sul cluster di database. Il cluster non distinguerà se viene eseguito sul database primario o su un database secondario. Se il cluster esegue questo comando rispetto al database primario, non sarà possibile eseguire scritture fino al completamento del dump e ciò potrebbe influire sulle prestazioni e sulla stabilità del sito.

L&#39;intero comando potrebbe essere simile al seguente:

```sql
mysqldump -h <host> -u <username> -p <password> --single-transaction <db_name> | gzip > /tmp/<dump_name>.sql.gz
```

Il backup del database creato eseguendo il comando `mysqldump` e salvato in `\tmp` deve essere spostato da questa posizione. Non deve occupare spazio di archiviazione in `\tmp` (il che potrebbe causare problemi).

+++

Per ottenere le credenziali DB (host, nome utente e password), è possibile chiamare la variabile di ambiente `MAGENTO_CLOUD_RELATIONSHIPS`:

```
echo $MAGENTO_CLOUD_RELATIONSHIPS |base64 --d |json_pp
```

**Documentazione correlata:**

* [mysqldump - Un programma di backup del database](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html) nella documentazione ufficiale di MySQL.
* [Variabili specifiche per il cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud.html) (vedere `MAGENTO_CLOUD_RELATIONSHIPS`) nella guida Commerce on Cloud Infrastructure.
