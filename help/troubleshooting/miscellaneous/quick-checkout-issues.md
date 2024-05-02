---
title: Risoluzione dei problemi di Check-Out rapido
description: In questo articolo vengono illustrati i problemi che possono verificarsi durante l’utilizzo dell’estensione Quick Checkout for Adobe Commerce e vengono fornite soluzioni per risolverli in modo da poter utilizzare correttamente l’estensione.
exl-id: 8ab46318-d62a-4b7e-bbe5-4c52cfeb9e36
feature: Checkout, Orders
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# Risoluzione dei problemi di Check-Out rapido

In questo articolo vengono illustrati i problemi che possono verificarsi durante l’utilizzo dell’estensione Quick Checkout for Adobe Commerce e vengono fornite soluzioni per risolverli in modo da poter utilizzare correttamente l’estensione.

## Prodotti e versioni interessati

* Il [Pagamento rapido](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/overview.html) è compatibile sia con il Magento Open Source che con Adobe Commerce. Consulta [Ciclo di vita](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/lifecycle-policy.html) per ulteriori informazioni sulle versioni supportate.

## Tasti compositore errati e stabilità minima per `RC`

<u>Causa</u>:

Se viene visualizzato il messaggio di errore seguente, è possibile che siano presenti chiavi di composizione non corrette:

```terminal
Could not find a matching version of package magento/quick-checkout. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (RC).
```

<u>Soluzione</u>:

Verifica che le chiavi del compositore siano collegate a _ID MAGENTO_ utilizzato durante la registrazione Quick Checkout.

Per visualizzare le chiavi del compositore configurate:

1. Trova la posizione del `auth.json` file:

   ```bash
   composer config --global home
   ```

1. Visualizza `auth.json` file:

   ```bash
   cat /path/to/auth.json
   ```

1. Consulta [quali chiavi sono associate al tuo ID Magento](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html).

1. Imposta stabilità minima su `RC` nel `composer.json` file.

   ```json
   "minimum-stability": "RC"
   ```

## Memoria insufficiente per PHP

<u>Causa</u>:

Se viene visualizzato il seguente messaggio di errore che indica che non si dispone di memoria sufficiente per PHP:

```terminal
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

<u>Soluzione</u>:

[Aumentare il limite di memoria](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html#increase-php-memory-limit) per PHP sul tuo ambiente in `php.ini`.

In alternativa, è possibile specificare il limite di memoria utilizzando questo comando: `php -d memory_limit=-1 [path to composer]/composer require magento/quick-checkout`.

Ad esempio:

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/quick-checkout
```

## Aggiungi righe indirizzo con un nuovo indirizzo di spedizione

Si è verificato un problema noto per l’estensione Quick Checkout.

Quando [accedi con un account Bolt](https://help.bolt.com/shoppers/guides/checkout/log-in/), è possibile aggiungere un nuovo indirizzo di spedizione con un limite di 4 righe per indirizzo stradale.

Se il nuovo indirizzo di spedizione contiene più di 4 righe, non verrà memorizzato.

Adobe Commerce in genere può essere configurato per supportare fino a 20 righe di indirizzo stradale.

## Comportamento imprevisto quando `Display Billing Address On` è impostato su `payment page`

Si è verificato un problema noto per l’estensione Quick Checkout.

Se si imposta `Display Billing Address On` parametro per `payment page` e [accedi con un account Bolt](https://help.bolt.com/shoppers/guides/checkout/log-in/) quando si controlla `My billing and shipping address are the same` , viene visualizzato il pulsante di opzione `use existing card`. Poiché l’indirizzo di fatturazione è applicabile solo alle nuove carte di credito, non sarà visibile fino a quando l’utente Bolt non deciderà di aggiungere una nuova opzione per la carta di credito.

Consulta la [Pagamento](https://docs.magento.com/user-guide/configuration/sales/checkout.html) per ulteriori informazioni su `Display Billing Address On` parametro.
