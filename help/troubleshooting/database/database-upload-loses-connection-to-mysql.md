---
title: Il caricamento del database perde la connessione a MySQL
description: Questo articolo fornisce una soluzione per i casi in cui il caricamento del database perde la connessione a MySQL.
exl-id: 6051cea1-8292-4a81-8908-eb516cb4a32b
feature: Services
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# Il caricamento del database perde la connessione a MySQL

Questo articolo fornisce una soluzione per i casi in cui il caricamento del database perde la connessione a MySQL.

## Prodotti e versioni interessati

Adobe Commerce sull’infrastruttura cloud 2.2.x., 2.3.x

## Problema

Il database non viene caricato nei rami primario/di integrazione su Adobe Commerce su infrastruttura cloud Architettura del piano Pro o in qualsiasi ramo su Adobe Commerce su infrastruttura cloud Architettura del piano Starter, con il sintomo dell’impossibilità di connettersi. Questo errore viene visualizzato nella CLI.

```
web@ddc35c264bd89a72042f1f3e5a:~$ mysql -h database.internal -u user -p main
Enter password:
ERROR 2013 (HY000): Lost connection to MySQL server at 'reading initial communication packet', system error: 0 "Internal error/check (Not system error)"
```

## Causa

Ciò è in genere dovuto alla mancanza di spazio su disco per l&#39;importazione del database.

## Soluzione

Verificare se lo spazio su disco è insufficiente. Per eseguire questa operazione, eseguire il comando `netcat` in CLI sulla porta di database 3306. Se il disco è pieno, verrà visualizzato un messaggio completo:

```
web@ddc35c264bd89a72042f1f3e5a:~$ nc database.internal 3306
Database out of space
```

Sarà necessario allocare più spazio per il database in `services.yaml` e distribuire se si dispone di spazio inutilizzato. Per i passaggi, vedere [Spazio su disco di servizio](https://devdocs.magento.com/cloud/project/manage-disk-space.html#service-disk-space).

Nota: nel piano dell&#39;architettura Pro, è possibile controllare lo spazio allocato nella partizione eseguendo il comando seguente: `df -h`

È previsto un output simile al seguente. In questo esempio, vengono utilizzati 10 GB dei 25 GB allocati, mentre 15 GB di spazio MySQL non vengono utilizzati.

```
f240jestone3wt@i-087r2a25fdac80726:~$ df -h|grep 'File\|xvd'
Filesystem                                         Size  Used Avail Use% Mounted on
/dev/xvda1                                          59G   15G   42G  26% /
/dev/xvdj                                           25G   10G   15G  41% /data/mysql
/dev/xvdi                                           25G   22G  2.6G  90% /data/exports
```

## Lettura correlata

[Gestione spazio su disco](https://devdocs.magento.com/cloud/project/manage-disk-space.html) nella documentazione per gli sviluppatori
