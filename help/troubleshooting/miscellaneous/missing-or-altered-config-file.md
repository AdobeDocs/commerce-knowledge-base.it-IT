---
title: File di configurazione mancante o modificato
description: Risolvi il problema relativo a file di configurazione mancanti o modificati per Adobe Commerce.
exl-id: d80bf981-8ba6-4357-a841-57bf5d3f2a3f
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---

# File di configurazione mancante o modificato

Questo articolo illustra come risolvere il problema relativo alla modifica o all’assenza dei file di configurazione.

## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud, tutte le versioni

## Problema

I file di configurazione `config.php` e/o `env.php` sono stati modificati in modo errato o sono mancanti.

## Soluzione

Il processo di distribuzione crea un file di backup per ciascun file di configurazione:

* `app/etc/config.php.bak` — contiene impostazioni specifiche del sistema e viene generato automaticamente durante la compilazione se non esiste
* `app/etc/env.php.bak` — contiene dati di configurazione sensibili

È possibile ripristinarli utilizzando il comando ECE-tools `backup:restore`.

I file BAK sono un prodotto del processo di distribuzione. Se si modifica manualmente un file di configurazione dopo la distribuzione, le modifiche non verranno applicate ai file BAK esistenti.

Per ripristinare i file di configurazione:

1. Accedi al tuo archivio remoto utilizzando [SSH](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections#ssh).
1. Elencare i file di backup disponibili.

   ```
   ./vendor/bin/ece-tools backup:list
   ```

   ```
   The list of backup files:
   app/etc/env.php
   app/etc/config.php
   ```

1. Ripristinare i file di configurazione.

   ```
   ./vendor/bin/ece-tools backup:restore
   ```

   Viene visualizzato un elenco dei file di configurazione esistenti interessati dal ripristino.

   ```
   app/etc/env.php file exists! If you want to rewrite existed files use --force
   app/etc/config.php file exists! If you want to rewrite existed files use --force
   ```

1. Utilizzare l&#39;opzione `--force` per sovrascrivere tutti i file.

   ```
   ./vendor/bin/ece-tools backup:restore --force
   ```

   ```
   Command backup:restore with option --force will rewrite your existed files. Do you want to continue [y/N]?y
   Backup file app/etc/env.php was restored.
   Backup file app/etc/config.php was restored.
   ```

1. In alternativa, è possibile ripristinare un file di configurazione specifico.

   ```
   ./vendor/bin/ece-tools backup:restore --force --file=app/etc/config.php
   ```

   ```
   Command backup:restore with option --force will rewrite your existed files. Do you want to continue [y/N]?y
   Backup file app/etc/config.php was restored.
   ```
