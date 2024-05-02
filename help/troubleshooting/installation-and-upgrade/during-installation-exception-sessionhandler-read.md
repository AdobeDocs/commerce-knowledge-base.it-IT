---
title: Durante l'installazione, eccezione SessionHandler::read()
description: "Questo articolo corregge un errore di eccezione **SessionHandler::read()** durante l’installazione di Adobe Commerce."
source-git-commit: 5cec04f8c4f80d34fc26b06eb929960ce21e2dc0
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---


# Durante l&#39;installazione, eccezione SessionHandler::read()

Questo articolo fornisce una correzione per un’eccezione **SessionHandler::read()** durante l’installazione di Adobe Commerce.

## Problema

Nell’ultimo passaggio dell’installazione di Adobe Commerce viene visualizzata la seguente eccezione:

```temrinal
exception 'Exception' with message 'Warning: SessionHandler::read():
open(..) failed: No such file or directory (2) ../magento2/lib/internal/Magento/Framework/Session/SaveHandler.php on line 74'
in ../magento2/lib/internal/Magento/Framework/App/ErrorHandler.php:67
```

>[!NOTE]
>
>Questo errore si verifica solo nelle versioni dei codici precedenti al 28 settembre 2015. Se installi un codice datato 29 settembre o successivo, questo errore non dovrebbe verificarsi. Per ulteriori informazioni sulle opzioni di configurazione per Redis, consulta [Configurare Redis](https://devdocs.magento.com/guides/v2.3/config-guide/redis/config-redis.html) nella documentazione per gli sviluppatori. Per ulteriori informazioni su come specificare Redis utilizzando il programma di installazione della riga di comando, vedere [argomento di installazione](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-install.html) o [argomento di configurazione della distribuzione](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-subcommands-deployment.html#instgde-cli-subcommands-configphp) nella documentazione per gli sviluppatori.

## Causa

Questo accade quando `session.save_handler` Il parametro PHP è impostato su un&#39;archiviazione di sessione diversa da `files` (ad esempio, `redis`, `memcached`e così via). Questo è un problema noto che stiamo lavorando per risolvere.

## Soluzioni:

* Aggiorna il codice Adobe Commerce. Fai riferimento a [Guida all&#39;installazione > Aggiornare il software Adobe Commerce](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-uninstall.html#instgde-install-magento-update) nella documentazione per gli sviluppatori.
* Utilizza la seguente soluzione alternativa con il codice esistente:

## Individua `php.ini` {#locate-php-ini}

Individua `php.ini` immettendo il comando seguente:

```php
php -i | grep "Loaded Configuration File"
```

Seguono le posizioni tipiche:

* Ubuntu: `/etc/php5/cli/php.ini`
* CentOS: `/etc/php.ini`

## Soluzione alternativa {#workaround}

1. Come utente con `root` privilegi, apertura `php.ini` in un editor di testo.
1. Individua `session.save_handler`
1. Impostalo in uno dei seguenti modi:
   * Per aggiungere un commento:

     ```php
     ;session.save_path = <path>
     ```

   * Per impostarlo su un percorso del file system:

     ```php
     session.save_handler = files
     ```
