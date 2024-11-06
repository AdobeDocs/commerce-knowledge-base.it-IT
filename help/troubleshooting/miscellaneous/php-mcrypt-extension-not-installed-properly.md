---
title: Estensione PHP Mcrypt non installata correttamente
description: Estensione PHP Mcrypt non installata correttamente
exl-id: 1010349e-6631-4a05-8883-5cc903d67534
feature: Extensions, Install
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---

# Estensione PHP Mcrypt non installata correttamente

>[!WARNING]
>
>NOTA: la funzionalità della libreria mcrypt è stata [rimossa da PHP 7.1 ed è stata rimossa da PHP 7.2](https://www.php.net/manual/en/intro.mcrypt.php).

## Dettaglio

Gli errori possono includere quanto segue:

```php
exception 'Exception' with message 'PHP Warning: PHP Startup: Unable to load dynamic library '/usr/lib/php5/20121212/mcrypt.so' - /usr/lib/php5/20121212/mcrypt.so: cannot open shared object file: No such file or directory
```

```php
Installing data fixtures:
/usr/bin/php -f '/Users/username/www/magento/dev/shell/run_data_fixtures.php' -- --bootstrap='MAGE_DIRS[base][path]=/Users/username/www/magento' 2>&1
[ERROR] exception 'Exception' with message '
Fatal error: Uncaught exception 'Exception' with message 'Module 'Magento_Core' depends on 'mcrypt' PHP [extension](https://experienceleague.adobe.com/en/docs/commerce-operations/operational-playbook/glossary#extension) that is not loaded.'
```

```php
======================================================================
   The application has thrown an exception!
======================================================================
 Magento\Framework\Exception
 Command returned non-zero exit code:
`/usr/bin/php5 -f '/var/www/magento2/dev/shell/run_data_fixtures.php' -- --bootstrap='MAGE_DIRS[base][path]=/var/www/magento2' 2>&1`
```

## Descrizione

Soprattutto nei sistemi di sviluppo che includono uno &quot;stack&quot; Linux/Apache/MySQL/PHP (LAMP) separato dal sistema operativo, è possibile che mcrypt non sia installato o che sia installato nel percorso dello stack LAMP ma non nel percorso del sistema operativo.

Di conseguenza, il programma di installazione di Adobe Commerce non è in grado di individuare l’estensione e l’installazione non riesce.

## Suggerimento

Determina se l&#39;estensione mcrypt viene caricata in uno dei seguenti modi:

* Configura un file [phpinfo.php](http://kb.mediatemple.net/questions/764/How+can+I+create+a+phpinfo.php+page%3F#gs) nella directory principale del server Web ed esamina l&#39;output in un browser Web.
* Esegui il comando seguente:    `$ php -r "phpinfo();" | grep mcrypt`

Se mcrypt è installato *not*, vengono visualizzati messaggi simili a quelli riportati di seguito:

```php
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20121212/mcrypt.so' - /usr/lib/php5/20121212/mcrypt.so: cannot open shared object file: No such file or directory in Unknown on line 0
```

In alcuni casi, potrebbe essere necessario installare il software Adobe Commerce dalla [riga di comando](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/advanced) e specificare il percorso completo dello stack LAMP in cui è installato mcrypt.
