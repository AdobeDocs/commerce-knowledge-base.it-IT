---
title: Creazione di un dump del database sull’infrastruttura cloud di Adobe Commerce
description: Questo articolo illustra i modi possibili (e consigliati) per creare un’immagine database (DB) su Adobe Commerce nell’infrastruttura cloud.
exl-id: 4a2e54ac-8d65-4e51-8337-08f9748dc6c0
feature: Cloud
source-git-commit: 0948b2a94ee4f2a355e7c024a09929f0ad223783
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# Creazione di un dump del database sull’infrastruttura cloud di Adobe Commerce

Questo articolo illustra i modi possibili (e consigliati) per creare un’immagine database (DB) su Adobe Commerce nell’infrastruttura cloud.

Per scaricare il database è sufficiente utilizzare una sola variante (opzione). Queste opzioni si applicano a qualsiasi tipo di ambiente (integrazione, staging, produzione) e a qualsiasi piano (Adobe Commerce su infrastruttura cloud Architettura del piano Starter e Adobe Commerce su infrastruttura cloud Architettura del piano Pro).

## Prerequisito: SSH per l’ambiente

Per eseguire il dump del database su Adobe Commerce sull’infrastruttura cloud con le varianti descritte in questo articolo, devi prima [SSH per l’ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).

>[!WARNING]
>
>Se si sceglie l&#39;opzione 1 o l&#39;opzione 2, eseguire il comando durante le ore non di punta su un nodo secondario del database.

## Opzione 1: db-dump (**strumenti ece; raccomandati**)

È possibile scaricare il database utilizzando [Utensili ECE](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html) comando:

```php
vendor/bin/ece-tools db-dump
```

Questa è l’opzione consigliata e più sicura.

Consulta [Eseguire il dump del database (ECE-Tools)](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/database-dump.html) nella Guida all’infrastruttura Commerce on Cloud.

## Opzione 2: mysqldump

>[!WARNING]
>
>Non eseguire questo comando sul cluster di database. Il cluster non distinguerà se viene eseguito sul database primario o su un database secondario. Se il cluster esegue questo comando rispetto al database primario, non sarà possibile eseguire scritture fino al completamento del dump e ciò potrebbe influire sulle prestazioni e sulla stabilità del sito.

È possibile scaricare il database utilizzando MySQL nativo `mysqldump` comando.

L&#39;intero comando potrebbe essere simile al seguente:

```sql
mysqldump -h <host> -u <username> -p <password> --single-transaction <db_name> | gzip > /tmp/<dump_name>.sql.gz
```

Backup del database creato eseguendo il comando `mysqldump` e salvato in `\tmp`, deve essere spostato da questa posizione. Non deve occupare spazio di archiviazione `\tmp` (che potrebbe causare problemi).

Per ottenere le credenziali DB (host, nome utente e password), è possibile chiamare `MAGENTO_CLOUD_RELATIONSHIPS` variabile di ambiente:

```
echo $MAGENTO_CLOUD_RELATIONSHIPS |base64 --d |json_pp
```

**Documentazione correlata:**

* [mysqldump - Un programma di backup del database](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html) nella documentazione ufficiale di MySQL.
* [Variabili specifiche per il cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud.html) (vedere `MAGENTO_CLOUD_RELATIONSHIPS`) nella nostra Guida all’infrastruttura Commerce on Cloud.
