---
title: Errori impostazioni PHP
description: Questo articolo fornisce soluzioni per gli errori delle impostazioni PHP.
exl-id: 51fb3c95-2e25-4d86-a6cf-e08e90d097ca
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
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
1. Individua il `php.ini` file utilizzando il comando seguente:

   ```
   bash    $ php --ini
   ```

1. Come utente con `root` , utilizza un editor di testo per aprire `php.ini` specificato da `Loaded Configuration File`.
1. Individua `memory_limit`.
1. Cambialo in un valore di `2GB` per l&#39;uso normale e il debug.
1. Salva le modifiche apportate a `php.ini` ed esci dall’editor di testo.
1. Riavvia il server web. Di seguito sono riportati alcuni esempi:

   * CentOS: `service httpd restart`
   * Ubuntu: `service apache2 restart`
   * nginx (sia CentOS che Ubuntu): `service nginx restart`

1. Riprovare l&#39;installazione.

## errore max-input-vars dovuto a moduli di grandi dimensioni

Configurazioni con un numero elevato di visualizzazioni, prodotti, attributi o opzioni possono generare moduli che superano il limite PHP preimpostato. Se il numero di valori inviati supera il `max-input-vars` limite impostato entro `php.ini` (il valore predefinito è 1000), i dati rimanenti non vengono trasferiti e i valori del database non vengono aggiornati. In questo caso, nel registro PHP viene visualizzato un avviso:

```terminal
PHP message: PHP Warning: Unknown: Input variables exceeded 1000. To increase the limit change max_input_vars in php.ini.
```

Nessun valore &quot;corretto&quot; per `max-input-vars`; dipende dalle dimensioni e dalla complessità della configurazione. Modifica il valore in `php.ini` file in base alle esigenze. Consulta [Impostazioni PHP richieste](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html).

## errore del livello massimo di nidificazione delle funzioni xdebug

Consulta [Durante l&#39;installazione, errore del livello massimo di nidificazione della funzione xdebug](/help/troubleshooting/miscellaneous/installation-xdebug-maximum-function-nesting-level-error.md).

## Gli errori vengono visualizzati quando si accede a un modello PHTML

Il testo di errore è in genere:

```terminal
Parse error: syntax error, unexpected 'data' (T_STRING)
```

### Soluzione: set `asp_tags = off` in php.ini

Più modelli hanno una sintassi per il supporto del livello astratto nei modelli (utilizzano diversi motori di modelli come Twig) racchiusi in `<% %>` tag, come questo [modello](https://github.com/magento/magento2/blob/2.0/app/code/Magento/Catalog/view/adminhtml/templates/product/edit/base_image.phtml) per visualizzare un’immagine del prodotto:

```php
<img
    class="product-image"
    src="<%- data.url %>"
    data-position="<%- data.position %>"
    alt="<%- data.label %>" />
```

Ulteriori informazioni su [asp\_tags](http://php.net/manual/en/ini.core.php#ini.asp-tags).

Modifica `php.ini` e imposta `asp_tags = off`. Per ulteriori informazioni, consulta [Impostazioni PHP richieste](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html).
