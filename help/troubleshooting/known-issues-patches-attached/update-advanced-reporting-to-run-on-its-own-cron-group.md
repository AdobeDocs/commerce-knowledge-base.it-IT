---
title: Aggiornare il reporting avanzato in modo che venga eseguito sul proprio gruppo cron
description: Questo articolo fornisce una patch per il problema noto per Adobe Commerce sull’infrastruttura cloud 2.3.0, in cui il reporting avanzato non mostra alcun dato. Questo perché il processo di Reporting avanzato "analytics_collect_data" non viene eseguito in base alla pianificazione. Questo articolo fornisce una patch che creerà un gruppo cron di reportistica avanzata "analytics".
exl-id: 8aff9e2b-d9be-4136-975b-05963e23f55c
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%

---

# Aggiornare il reporting avanzato in modo che venga eseguito sul proprio gruppo cron

Questo articolo fornisce una patch per il problema noto per Adobe Commerce sull’infrastruttura cloud 2.3.0, in cui il reporting avanzato non mostra alcun dato. Il processo di Reporting avanzato `analytics_collect_data` non viene eseguito in base alla pianificazione. Questo articolo fornisce una patch che creerà un gruppo cron di Reporting avanzato `analytics`.

## Problema

Nessun dato viene caricato nel modulo di reporting avanzato.

## Patch

La patch è allegata a questo articolo. La patch sposta le attività del processo cron `analytics` dal gruppo predefinito in `analytics`.

Per scaricarlo, scorri verso il basso fino alla fine dell’articolo e fai clic sul nome del file, oppure fai clic sul seguente collegamento:

[MDVA-19640\_EE\_2.3.0\_COMPOSER\_v1.patch](assets/MDVA-19640_EE_2.3.0_COMPOSER_v1.patch.zip)

Dopo aver applicato la patch, eseguire la seguente query SQL. È necessario eseguire la query per modificare i record nella tabella `cron_schedule`.

```
UPDATE core_config_data
SET `path` = REPLACE(path, "crontab/default/jobs/analytics", "crontab/analytics/jobs/analytics")
WHERE `path` LIKE "crontab/default/jobs/analytics%";
```

### Versioni compatibili di Adobe Commerce:

La patch è stata creata per

* Adobe Commerce sull’infrastruttura cloud 2.3.0

La patch è compatibile (ma potrebbe non risolvere il problema) anche con le seguenti versioni ed edizioni di Adobe Commerce: 2.2.2-2.2.10, 2.3.0-2.3.2 e 2.3.2-p2 e 2.3.3, per Adobe Commerce on-premise e Adobe Commerce on cloud infrastructure

## Come applicare il cerotto

Per istruzioni, vedere [Come applicare una patch del compositore fornita dall&#39;Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md).

## File allegati
