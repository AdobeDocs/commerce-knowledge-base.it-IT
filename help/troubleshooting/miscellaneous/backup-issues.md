---
title: Problemi di backup
description: Questo articolo elenca le possibili soluzioni per i problemi di creazione del backup.
exl-id: 1a6204ad-bd5a-46dc-8a8e-39655a174e09
feature: Storage, Data Import/Export
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# Problemi di backup

Questo articolo elenca le possibili soluzioni per i problemi di creazione del backup.

## Prodotti e versioni interessati

* Adobe Commerce on-premise 2.3.x
* Magento Open Source 2.3.x

## Backup disabilitato {#backup-disabled}

Se la funzionalità di backup di Adobe Commerce non si avvia o visualizza il seguente messaggio, è necessario abilitare la funzione prima di eseguire il backup.

```bash
Backup functionality is disabled.
Backup functionality is currently disabled. Please use other means for backups.
```

Immettere il seguente comando CLI:

```bash
bin/magento config:set system/backup/functionality_enabled 1
```

Per ulteriori informazioni sui backup, vedere [Eseguire il backup e il rollback del file system, del supporto e del database.](https://experienceleague.adobe.com/it/docs/commerce-operations/installation-guide/tutorials/backup)

## Spazio su disco insufficiente {#insufficient-disk-space-trouble-backup-space-}

Se il backup non è riuscito a causa di spazio su disco insufficiente, in genere è necessario liberare spazio su disco spostando alcuni file in un altro dispositivo o unità di archiviazione. Tuttavia, potrebbero esserci altri modi per risolvere il problema. Consulta una delle seguenti risorse per suggerimenti:

* [8 suggerimenti per risolvere i problemi relativi al disco rigido dei sistemi Linux e Unix, ad esempio Disco pieno o Impossibile scrivere sul disco](https://www.cyberciti.biz/datacenter/linux-unix-bsd-osx-cannot-write-to-hard-disk)
* [errore server: df indica che il disco è pieno, ma non lo è](https://serverfault.com/questions/315181/df-says-disk-is-full-but-it-is-not)
* [unix.stackexchange.com: rilevamento dello spazio su disco disponibile su Linux?](https://unix.stackexchange.com/questions/125429/tracking-down-where-disk-space-has-gone-on-linux)

## Errore del sistema operativo {#operating-system-error-trouble-backup-os-}

Sfortunatamente, non possiamo consigliare nulla di specifico a causa della varietà di errori che si potrebbero incontrare. Possiamo suggerirti, tuttavia:

* Contattare l&#39;amministratore di sistema.
* Cerca nei forum pubblici come [Stack Exchange](https://unix.stackexchange.com) o [Stack Overflow](https://stackoverflow.com)
* Apri un [problema GitHub](https://github.com/magento/magento2/issues) e proveremo ad aiutarti.

## Backup non riuscito {#backup-fails-trouble-backup-all-}

Se il backup non riesce o se tutti i test di backup non riescono, è possibile che il [proprietario del file system Adobe Commerce](https://experienceleague.adobe.com/it/docs/commerce-operations/installation-guide/prerequisites/file-system/overview) non disponga di privilegi e proprietà sufficienti per il file system Adobe Commerce. Ad esempio, un altro utente potrebbe essere il proprietario dei file o i file potrebbero essere di sola lettura.

Prestare particolare attenzione alle autorizzazioni del file system e alla proprietà della directory e delle sottodirectory `<magento_root>/var`. Per ulteriori informazioni, vedere [Impostare le autorizzazioni e la proprietà del file system](https://experienceleague.adobe.com/it/docs/commerce-operations/installation-guide/prerequisites/file-system/configure-permissions).
