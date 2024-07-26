---
title: Errori impostazioni PHP
description: Questo articolo fornisce soluzioni per gli errori delle impostazioni PHP.
exl-id: 51fb3c95-2e25-4d86-a6cf-e08e90d097ca
feature: Configuration
role: Developer
source-git-commit: 35d4f2130d0ec71f71f5f20aa8a7c76207e7a35a
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# Errori impostazioni PHP

Questo articolo fornisce soluzioni per gli errori delle impostazioni PHP.

## Errore limite memoria PHP

I controlli di fattibilità assicurano che siano stati impostati almeno 1 GB di memoria per i processi PHP. Questa impostazione dovrebbe essere sufficiente per la maggior parte delle installazioni, inclusa l’installazione di dati di esempio facoltativi. Tuttavia, consigliamo almeno 2 GB per il debug.

Per aumentare il limite di memoria PHP:

1. Accedi al server Adobe Commerce.
1. Individuare il file `php.ini` utilizzando il comando seguente:

   ```
   bash    $ php --ini
   ```

1. In qualità di utente con privilegi di `root`, utilizza un editor di testo per aprire `php.ini` specificato da `Loaded Configuration File`.
1. Individuare `memory_limit`.
1. Modificare il valore in `2GB` per l&#39;utilizzo normale e il debug.
1. Salvare le modifiche apportate a `php.ini` e uscire dall&#39;editor di testo.
1. Riavvia il server web. Di seguito sono riportati alcuni esempi:

   * CentOS: `service httpd restart`
   * Ubuntu: `service apache2 restart`
   * nginx (sia CentOS che Ubuntu): `service nginx restart`

1. Riprovare l&#39;installazione.

## errore max-input-vars dovuto a moduli di grandi dimensioni

Configurazioni con un numero elevato di visualizzazioni, prodotti, attributi o opzioni possono generare moduli che superano il limite PHP preimpostato. Se il numero di valori inviati supera il limite di `max-input-vars` impostato entro `php.ini` (il valore predefinito è 1000), i dati rimanenti non vengono trasferiti e i valori del database non vengono aggiornati. In questo caso, nel registro PHP viene visualizzato un avviso:

```bash
PHP message: PHP Warning: Unknown: Input variables exceeded 1000. To increase the limit change max_input_vars in php.ini.
```

Nessun valore &quot;corretto&quot; per `max-input-vars`. Dipende dalle dimensioni e dalla complessità della configurazione. Modificare il valore nel file `php.ini` in base alle esigenze. Vedere [Impostazioni PHP richieste](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html).

## errore del livello massimo di nidificazione delle funzioni xdebug

Vedere [Errore del livello massimo di nidificazione delle funzioni xdebug durante l&#39;installazione](/help/troubleshooting/miscellaneous/installation-xdebug-maximum-function-nesting-level-error.md).

## Gli errori vengono visualizzati quando si accede a un modello PHTML

Il testo di errore è in genere:

```bash
Parse error: syntax error, unexpected 'data' (T_STRING)
```

### Soluzione: impostare `asp_tags = off` in php.ini

Più modelli hanno una sintassi per il livello astratto di supporto nei modelli (utilizzano diversi motori di modelli come Twig) racchiusi tra `<% %>` tag, come questo [modello](https://github.com/magento/magento2/blob/2.0/app/code/Magento/Catalog/view/adminhtml/templates/product/edit/base_image.phtml) per la visualizzazione di un&#39;immagine di prodotto:

```php
<img
    class="product-image"
    src="<%- data.url %>"
    data-position="<%- data.position %>"
    alt="<%- data.label %>" />
```

Ulteriori informazioni su [asp\_tags](http://php.net/manual/en/ini.core.php#ini.asp-tags).

Modifica `php.ini` e imposta `asp_tags = off`. Per ulteriori informazioni, vedere [Impostazioni PHP richieste](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html).
