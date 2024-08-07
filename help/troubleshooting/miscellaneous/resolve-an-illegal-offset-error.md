---
title: Risolvi un errore di offset non valido
description: Questo articolo fornisce una soluzione per quando, in Adobe Commerce 2.1 o versione successiva, si riceve un messaggio di errore Risolvi un offset non valido durante la creazione di un nuovo prodotto in Commerce Admin.
exl-id: 62d16d3c-7f4b-45e9-ae4b-fe2b58cc3620
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# Risolvi un errore di offset non valido

Questo articolo fornisce una soluzione per quando, in Adobe Commerce 2.1 o versione successiva, si riceve un messaggio di errore Risolvi un offset non valido durante la creazione di un nuovo prodotto in Commerce Admin.

In Adobe Commerce 2.1 o versione successiva, quando si crea un nuovo prodotto in Commerce Admin, potrebbe essere visualizzato il seguente errore:

```text
Warning: Illegal string offset 'is_in_stock' in [...]/vendor/
magento/module-catalog-inventory/Ui/DataProvider/Product/Form/
Modifier/AdvancedInventory.php on line 87
```

## Dettaglio

Adobe Commerce 2.1 e versioni successive utilizzano i commenti del codice PHP nella chiamata di convalida `getDocComment` nel metodo [`getExtensionAttributes`](https://github.com/magento/magento2/blob/2.3/lib/internal/Magento/Framework/Api/ExtensionAttributesFactory.php#L64-L73) in `Magento\Framework\Api\ExtensionAttributesFactory.php`.

Se è stata abilitata la PHP OPcache (scelta consigliata), questo errore viene visualizzato perché per impostazione predefinita l&#39;impostazione OPcache [`opcache.save_comments`](http://php.net/manual/en/opcache.configuration.php#ini.opcache.save_comments) è disabilitata.

## Soluzione alternativa

Per risolvere il problema, individuare le impostazioni di configurazione di OPcache e abilitare `opcache.save_comments` come segue:

### Passaggio 1: individuare la configurazione OPcache

#### Per trovare le impostazioni di configurazione di OPcache:

Le impostazioni PHP OPcache si trovano in genere in `php.ini` o `opcache.ini`. La posizione potrebbe dipendere dal sistema operativo in uso e dalla versione PHP. Il file di configurazione OPcache potrebbe avere una sezione `[opcache]` o impostazioni come `opcache.enable`.

Utilizza le seguenti linee guida per trovarlo:

* Server web Apache:<br>

Per Ubuntu con Apache, le impostazioni OPcache si trovano in genere in `php.ini`.<br>
Per CentOS con Apache o nginx, le impostazioni OPcache si trovano in genere in `/etc/php.d/opcache.ini`.<br>
In caso contrario, utilizzare il comando seguente per individuarlo:

```bash
    $ sudo find / -name 'opcache.ini'
```

* Server Web nginx con PHP-FPM: `/etc/php5/fpm/php.ini`.

Se si dispone di più di un `opcache.ini`, modificarli tutti.


### Passaggio 2: abilitare `opcache.save_comments`

1. Apri il file di configurazione OPcache in un editor di testo.
1. Individuare `opcache.save_comments` e, se necessario, rimuoverlo dal commento.
1. Assicurarsi che il relativo valore sia impostato su `1`.
1. Salva le modifiche e esci dall’editor di testo.
1. Riavviare il server Web:

   * Apache, Ubuntu: `service apache2 restart`
   * Apache, CentOS: `service httpd restart`
   * nginx, Ubuntu e CentOS: `service nginx restart`

1. Rigenera la configurazione DI e tutte le classi mancanti che possono essere generate automaticamente:

```bash
    $ bin/magento setup:di:compile`
```
