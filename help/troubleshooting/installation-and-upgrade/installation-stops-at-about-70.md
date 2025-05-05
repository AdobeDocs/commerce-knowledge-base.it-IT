---
title: L'installazione si arresta a circa il 70%
description: Questo articolo fornisce una correzione per i casi in cui l’installazione si interrompe a circa il 70%.
exl-id: 04aa3572-3c42-4565-9f7f-b4d90df96df2
feature: Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---

# L&#39;installazione si arresta a circa il 70%

Questo articolo fornisce una correzione per i casi in cui l’installazione si interrompe a circa il 70%.

## Problema

Durante l&#39;installazione tramite l&#39;Impostazione guidata, il processo si arresta a circa il 70% (con o senza dati di esempio). Sullo schermo non viene visualizzato alcun errore.

## Causa

Le cause comuni di questo problema includono:

* Impostazione PHP per [`max_execution_time`](http://php.net/manual/en/info.configuration.php#ini.max-execution-time)
* Valori di timeout per indice e vernice

## Soluzione:

Impostare tutte le opzioni seguenti in base alle esigenze.

### Tutti i server web e Vernice {#all-web-servers-and-varnish}

1. Individua `php.ini` utilizzando un file [`phpinfo.php`](https://experienceleague.adobe.com/it/docs/commerce-operations/installation-guide/prerequisites/optional-software).
1. In qualità di utente con privilegi di `root`, apri `php.ini` in un editor di testo.
1. Individuare l&#39;impostazione `max_execution_time`.
1. Cambia il valore in `18000`.
1. Salvare le modifiche apportate a `php.ini` e uscire dall&#39;editor di testo.
1. Riavvia Apache:

   * CentOS: `service httpd restart`
   * Ubuntu: `service apache2 restart`

   Se usa vernice o vernice, proceda come segue.

### Solo indice {#nginx-only}

Se utilizzi nginx, utilizza le impostazioni di timeout incluse in `nginx.conf.sample` o aggiungi le impostazioni di timeout nel file di configurazione dell&#39;host nginx alla sezione `location ~ ^/setup/index.php` come segue:

```php
location ~ ^/setup/index.php {
    .....................
    fastcgi_read_timeout 600s;
       fastcgi_connect_timeout 600s;
}
```

Inginx di riavvio: `service nginx restart`

### Solo vernice {#varnish-only}

Se si utilizza Vernice, modificare `default.vcl` e aggiungere un valore di limite di timeout alla stanza `backend` nel modo seguente:

```php
backend default {
.....................
      .first_byte_timeout = 600s;
}
```

Riavviare la vernice.

```php
service varnish restart
```
