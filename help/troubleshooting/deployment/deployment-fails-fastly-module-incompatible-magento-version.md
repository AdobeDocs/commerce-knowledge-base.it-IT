---
title: La distribuzione non riesce La versione di Adobe Commerce non compatibile con il modulo Fastly
description: AGGIORNATO IL 29 FEBBRAIO 2019
exl-id: aab77407-94e5-42de-92f4-2f0c19e24fa4
feature: Deploy, Extensions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# La distribuzione non riesce La versione di Adobe Commerce non compatibile con il modulo Fastly

AGGIORNATO IL 29 FEBBRAIO 2019

Questo articolo corregge eventuali errori di distribuzione dovuti all’incompatibilità del modulo Fastly con la versione corrente di Adobe Commerce.

**Problema:** la distribuzione non riesce dopo un nuovo commit e un nuovo push, con un messaggio di errore simile al seguente:

>\[Eccezione\] Avviso: argomento 3 mancante per Fastly\\Cdn\\Plugin\\..., chiamato in /app/vendor/magento/framework/Interception/Interceptor.php ... e definito in /app/vendor/fastly/magento2/Plugin/ExcludeFilesFromMinification.php ...

**Causa:** modifiche non compatibili con le versioni precedenti nel modulo Fastly v1.2.79.

**Soluzione (temporanea):** aggiornare il modulo Fastly alla versione 1.2.82 o successiva e caricare una nuova VCL in Commerce Admin. Quindi, conferma e invia le modifiche per attivare una distribuzione corretta.

## Versioni interessate

* Adobe Commerce on-premise 2.1.X
* Adobe Commerce sull’infrastruttura cloud 2.1.X
* Modulo Fastly 1.2.79

## Problema

Quando esegui il commit e invii le modifiche all&#39;ambiente di integrazione, produzione o gestione temporanea, in genere il passaggio successivo consiste nell&#39;attivare il processo di distribuzione. Questa operazione viene eseguita automaticamente in Adobe Commerce on cloud infrastructure edition e manualmente in Adobe Commerce on-premise.

La distribuzione potrebbe non riuscire e presentare i seguenti messaggi di errore:

```
[2019-01-23 00:00:00] INFO: php ./bin/magento setup:static-content:deploy --ansi --no-interaction --jobs 1 --exclude-theme Magento/luma en_GB en_US
[2019-01-23 00:00:00] CRITICAL:
  Requested languages: en_GB, en_US
  Requested areas: frontend, adminhtml
  Requested themes: Magento/blank, Magento/backend
  === frontend -> Magento/blank -> en_GB ===

    [Exception]
    Warning: Missing argument 3 for Fastly\Cdn\Plugin\ExcludeFilesFromMinification::afterGetExcludes(), called in /app/vendor/magento/framework/Interception/Interceptor.php on line 152 and defined in /app/vendor/fastly/magento2/Plugin/ExcludeFilesFromMinification.php on line 38

  setup:static-content:deploy [-d|--dry-run] [--no-javascript] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [-t|--theme[="..."]] [--exclude-theme[="..."]] [-l|--language[="..."]] [--exclude-language[="..."]] [-a|--area[="..."]] [--exclude-area[="..."]] [-j|--jobs[="..."]] [--symlink-locale] [languages1] ... [languagesN]

[2019-01-23 000:00:00] INFO: Set flag: var/.deploy_is_failed
[2019-01-23 00:00:00] CRITICAL: Command php ./bin/magento setup:static-content:deploy --ansi --no-interaction --jobs 1 --exclude-theme Magento/luma en_GB en_US returned code 1
```

Se utilizzi la soluzione Adobe Commerce su infrastruttura cloud, visualizzerai questo messaggio di errore nel [registro di distribuzione](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations). Per Adobe Commerce on-premise, l’errore verrà visualizzato nella riga di comando.

## Causa

Il problema è causato dalle modifiche non compatibili con le versioni precedenti nel modulo Fastly v1.2.79.

## Soluzione

Aggiornare il modulo Fastly alla versione 1.2.82 o successiva.

A questo scopo, effettua le seguenti operazioni:

1. Eseguire uno dei seguenti comandi:
   * se il modulo Fastly è incluso in magento-cloud-metapackage:    <pre>aggiornamento compositore magento/magento-cloud-metapackage</pre>
   * se il modulo Fastly è stato installato separatamente (ad esempio, nel caso di utilizzo di Adobe Commerce on-premise, non dell’edizione cloud) <pre>aggiornamento rapido compositore/magento2</pre>
1. Esegui il commit e l’invio delle modifiche, quindi attiva il processo di distribuzione se non viene eseguito automaticamente.
1. In Admin, [carica il nuovo VCL in Fastly](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#upload-vcl-snippets).
