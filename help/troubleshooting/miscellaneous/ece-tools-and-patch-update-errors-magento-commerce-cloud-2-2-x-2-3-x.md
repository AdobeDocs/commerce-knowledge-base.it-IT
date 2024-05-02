---
title: Errori ECE-Tools e aggiornamento patch per l'infrastruttura cloud Adobe Commerce 2.2.x., 2.3.x
description: Questo articolo fornisce una soluzione per il problema che si verifica quando vengono visualizzati messaggi di errore, tra cui "*impossibile aprire il flusso:*" o "*Nessun file o directory di questo tipo*" durante il tentativo di distribuire aggiornamenti a ECE-Tools, patch o altre modifiche.
exl-id: b1658001-0ffd-4f8a-a15f-d785efcee51f
feature: Cloud, Paas
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---

# Errori ECE-Tools e aggiornamento patch per l&#39;infrastruttura cloud Adobe Commerce 2.2.x., 2.3.x

Questo articolo fornisce una soluzione per il problema in cui vengono visualizzati messaggi di errore, tra cui &quot;*impossibile aprire il flusso:*&quot; o &quot;*File o directory non presente*&quot; quando si tenta di distribuire aggiornamenti a strumenti ECE, patch o altre modifiche.

## Prodotti e versioni interessati

Adobe Commerce sull’infrastruttura cloud 2.2.x., 2.3.x

## Problema

Gli errori durante il tentativo di distribuire aggiornamenti a strumenti ECE, patch o altre modifiche includono: errori PHP nella console Cloud e nella `var/log/cloud.log`

```
W: PHP Warning: require(<path to file>): failed to open stream: No such file or directory in <path to file> on line 70
W: PHP Fatal error: require(): Failed opening required '<path to file>;'
(include_path='<path to file>') in <path to file> on line 70

Warning: require(/app/vendor/composer/../../app/etc/NonComposerComponentRegistration.php):
failed to open stream: No such file or directory in /app/vendor/composer/autoload_real.php
on line 70

Fatal error: require(): Failed opening required '/app/vendor/composer/../../app/etc/NonComposerComponentRegistration.php'
(include_path='/app/vendor/magento/zendframework1/library:.:/usr/share/php')
in /app/vendor/composer/autoload_real.php on line 70

E: Error building project: Step failed with status code 255.
```

Errori registro eccezioni:

```
CRITICAL:
error: <path to missing file>: No such file or directory
```

```
W: Generating optimized autoload files
W: PHP Warning: Uncaught ErrorException: require(<path to file>):
failed to open stream: No such file or directory in <path to file>
```

```
PHP Warning: Uncaught Exception: Warning: require(/app/setup/config/application.config.php):
failed to open stream: No such file or directory in /app/vendor/magento/framework/Console/Cli.php
on line 63 in /app/vendor/magento/framework/App/ErrorHandler.php:61
```

```
[Symfony\Component\Console\Exception\CommandNotFoundException]
 W: There are no commands defined in the "module" namespace.
```

## Causa

Configurazione errata del `composer.json` file.

## Soluzione

Se manca un&#39;impostazione `composer.json` , alcune directory non verranno copiate dalla Adobe Commerce Code Base. Impossibile applicare il pacchetto e l&#39;aggiornamento/patch. Impossibile trovare i file.

Modifica la sezione aggiuntiva in modo che corrisponda a quella fornita di seguito, quindi ripeti l’implementazione.

```
"extra":{
  "magento-force": true,
  "magento-deploystrategy": "copy"
}
```

## Lettura correlata

* [Aggiornamenti e patch](https://devdocs.magento.com/guides/v2.3/cloud/project/project-upgrade-parent.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=update%20ece%20tools) nella documentazione per gli sviluppatori.
