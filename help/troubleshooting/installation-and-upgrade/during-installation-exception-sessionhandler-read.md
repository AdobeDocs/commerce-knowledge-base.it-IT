---
title: Durante l'installazione, eccezione SessionHandler::read()
description: "Questo articolo corregge un errore di eccezione **SessionHandler::read()** durante l’installazione di Adobe Commerce."
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---


# Durante l&#39;installazione, eccezione SessionHandler::read()

Questo articolo fornisce una correzione per un errore **SessionHandler::read()** dell&#39;eccezione durante l&#39;installazione di Adobe Commerce.

## Problema

Nell’ultimo passaggio dell’installazione di Adobe Commerce viene visualizzata la seguente eccezione:

```temrinal
exception 'Exception' with message 'Warning: SessionHandler::read():
open(..) failed: No such file or directory (2) ../magento2/lib/internal/Magento/Framework/Session/SaveHandler.php on line 74'
in ../magento2/lib/internal/Magento/Framework/App/ErrorHandler.php:67
```

>[!NOTE]
>
>Questo errore si verifica solo nelle versioni dei codici precedenti al 28 settembre 2015. Se installi un codice datato 29 settembre o successivo, questo errore non dovrebbe verificarsi. Per ulteriori informazioni sulle opzioni di configurazione per Redis, vedi [Configurare Redis](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cache/redis/config-redis) nella documentazione per gli sviluppatori. Per ulteriori informazioni su come specificare Redis utilizzando il programma di installazione della riga di comando, vedere l&#39;[argomento sull&#39;installazione](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/advanced) o l&#39;[argomento sulla configurazione della distribuzione](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/deployment) nella documentazione per gli sviluppatori.

## Causa

Ciò si verifica quando il parametro PHP `session.save_handler` è impostato su un&#39;altra archiviazione di sessione diversa da `files` (ad esempio, `redis`, `memcached` e così via). Questo è un problema noto che stiamo lavorando per risolvere.

## Soluzioni:

* Aggiorna il codice Adobe Commerce. Consulta [Guida all&#39;installazione > Aggiornare il software Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/uninstall) nella documentazione per gli sviluppatori.
* Utilizza la seguente soluzione alternativa con il codice esistente:

## Individua `php.ini` {#locate-php-ini}

Individuare `php.ini` immettendo il comando seguente:

```php
php -i | grep "Loaded Configuration File"
```

Seguono le posizioni tipiche:

* Ubuntu: `/etc/php5/cli/php.ini`
* CentOS: `/etc/php.ini`

## Soluzione alternativa {#workaround}

1. In qualità di utente con privilegi di `root`, apri `php.ini` in un editor di testo.
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
