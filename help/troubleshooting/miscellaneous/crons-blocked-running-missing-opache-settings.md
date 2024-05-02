---
title: Cron si arresta a causa di configurazione errata o mancante [!DNL OpCache] impostazioni
description: Questo articolo fornisce una soluzione per i casi in cui i nodi smettono di funzionare a causa di configurazione errata o mancante [!DNL OpCache] impostazioni.
exl-id: 30643ea9-969f-41c8-8e62-b24e56d690cf
feature: Cache
role: Developer
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# Cron arrestato a causa di configurazione errata o mancante [!DNL OpCache] impostazioni

Questo articolo fornisce una soluzione per il caso in cui cron non funzioni più a causa di configurazione errata o mancante [!DNL OpCache] impostazioni.

## Prodotti e versioni interessati

Adobe Commerce sull’infrastruttura cloud, [tutte le versioni supportate](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problema

Il cron smise di funzionare.

## Causa

Il [!DNL OpCache] è stato aggiornato a una versione più recente che ha introdotto una [!DNL GraphQL] plug-in che riscrive il `env.php` in fase di esecuzione e potrebbe ignorare l’impostazione cron, che potrebbe aver causato il problema. Il [!DNL OpCache] è necessario aggiornare la configurazione per evitare problemi con il `env.php file`, e questo è stato risolto in [versione 2002.1.13](/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package.html?lang=en#v2002.1.13) del [!DNL ECE Tools] pacchetto.

## Soluzione

Opzione 1: eseguire quanto segue nello strumento della riga di comando:

```bash
bin/magento cron:run
```

È possibile che venga visualizzato un messaggio che informa che il cron è disabilitato.

Opzione 2: aprire `app/etc/env.php` file: se vedi quanto segue, significa che il cron è stato disabilitato manualmente, non è stato riabilitato a causa di una distribuzione non riuscita o che il problema era correlato al [!DNL OpCache] impostazioni.

```php
  'cron' =>
  array (
    'enabled' => 0,
  ),
```

1. Se il cron è disattivato, eseguire questo comando per riattivarlo: `vendor/bin/ece-tools cron:enable`
1. Assicurati di utilizzare l’ultima versione di [!DNL ECE Tools]. In caso contrario, eseguire l&#39;aggiornamento (o passare alla voce 3). Per verificare la versione esistente, esegui questo comando:
   `composer show magento/ece-tools`
1. Se ti trovi già nella versione più recente di [!DNL ECE Tools], verifica la presenza del `op-exclude.txt` file. A tale scopo, eseguire il comando seguente:
   `ls op-exclude.txt`.
Se questo file non è presente, aggiungi https://github.com/magento/magento-cloud/blob/master/op-exclude.txt all’archivio, quindi esegui il commit della modifica e la ridistribuzione.
1. Senza dover eseguire l&#39;aggiornamento [!DNL ECE Tools], puoi anche semplicemente aggiungere/modificare https://github.com/magento/magento-cloud/blob/master/op-exclude.txt nell’archivio, quindi confermare la modifica e ridistribuirla.

## Lettura correlata

* [Problemi relativi al controllo di preparazione al problema](/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-readiness-check-issues.html)
* [Crons, proprietà](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html)
* [Il processo Cron è bloccato nello stato &quot;in esecuzione&quot;](/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html)
