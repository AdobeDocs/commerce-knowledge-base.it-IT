---
title: Cron si arresta a causa di impostazioni non configurate o mancanti [!DNL OpCache]
description: In questo articolo viene fornita una soluzione per i casi in cui i nodi smettono di funzionare a causa di impostazioni non configurate o mancanti [!DNL OpCache] .
exl-id: 30643ea9-969f-41c8-8e62-b24e56d690cf
feature: Cache
role: Developer
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# Cron interrotta a causa di impostazioni [!DNL OpCache] non configurate o mancanti

Questo articolo fornisce una soluzione per il caso in cui cron non funzioni più a causa di impostazioni [!DNL OpCache] mancanti o non configurate correttamente.

## Prodotti e versioni interessati

Adobe Commerce su infrastruttura cloud, [tutte le versioni supportate](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problema

Il cron smise di funzionare.

## Causa

Il modulo [!DNL OpCache] è stato aggiornato a una versione più recente che ha introdotto un plug-in [!DNL GraphQL] che riscrive `env.php` in fase di esecuzione e potrebbe ignorare l&#39;impostazione cron, causando probabilmente il problema. È necessario aggiornare la configurazione di [!DNL OpCache] per evitare problemi con `env.php file` che sono stati risolti nella [versione 2002.1.13](/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package.html?lang=en#v2002.1.13) del pacchetto [!DNL ECE Tools].

## Soluzione

Opzione 1: eseguire quanto segue nello strumento della riga di comando:

```bash
bin/magento cron:run
```

È possibile che venga visualizzato un messaggio che informa che il cron è disabilitato.

Opzione 2: aprire il file `app/etc/env.php`. Se viene visualizzato quanto segue, il cron è stato disabilitato manualmente, non è stato riabilitato a causa di una distribuzione non riuscita o il problema era correlato alle impostazioni di [!DNL OpCache].

```php
  'cron' =>
  array (
    'enabled' => 0,
  ),
```

1. Se cron è disabilitato, eseguire questo comando per riabilitare cron: `vendor/bin/ece-tools cron:enable`
1. Assicurarsi di utilizzare la versione più recente di [!DNL ECE Tools]. In caso contrario, eseguire l&#39;aggiornamento (o passare alla voce 3). Per verificare la versione esistente, esegui questo comando:
   `composer show magento/ece-tools`
1. Se si utilizza già la versione più recente di [!DNL ECE Tools], verificare la presenza del file `op-exclude.txt`. A tale scopo, eseguire il comando seguente:
   `ls op-exclude.txt`.
Se questo file non è presente, aggiungi https://github.com/magento/magento-cloud/blob/master/op-exclude.txt all’archivio, quindi esegui il commit della modifica e la ridistribuzione.
1. Senza dover aggiornare [!DNL ECE Tools], puoi anche aggiungere/modificare https://github.com/magento/magento-cloud/blob/master/op-exclude.txt nel repository, quindi eseguire il commit della modifica e ridistribuirla.

## Lettura correlata

* [Problemi relativi al controllo di preparazione al problema](/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-readiness-check-issues.html)
* [Crons, proprietà](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html)
* [Il processo Cron è bloccato nello stato &quot;in esecuzione&quot;](/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html)
