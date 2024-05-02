---
title: L'installazione si arresta a circa il 70%
description: Questo articolo fornisce una correzione per i casi in cui l’installazione si interrompe a circa il 70%.
exl-id: 04aa3572-3c42-4565-9f7f-b4d90df96df2
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
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

1. Individua il `php.ini` utilizzando un [`phpinfo.php`](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/optional.html#install-optional-phpinfo) file.
1. Come utente con `root` privilegi, apertura `php.ini` in un editor di testo.
1. Individua il `max_execution_time` impostazione.
1. Modifica il valore in `18000` .
1. Salva le modifiche apportate a `php.ini` ed esci dall’editor di testo.
1. Riavvia Apache:

   * CentOS: `service httpd restart`
   * Ubuntu: `service apache2 restart`

   Se usa vernice o vernice, proceda come segue.

### Solo indice {#nginx-only}

Se utilizzi Inginx, utilizza il nostro `nginx.conf.sample` oppure aggiungi impostazioni di timeout nel file di configurazione dell&#39;host nginx al `location ~ ^/setup/index.php` come segue:

```php
location ~ ^/setup/index.php {
    .....................
    fastcgi_read_timeout 600s;
       fastcgi_connect_timeout 600s;
}
```

Inginx di riavvio: `service nginx restart`

### Solo vernice {#varnish-only}

Se si utilizza vernice, modificare `default.vcl` e aggiungi un valore limite di timeout al `backend` strofa come segue:

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
