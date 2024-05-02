---
title: Errore durante la distribuzione durante l’aggiornamento alla versione che supporta PHP 8.1
description: Questo articolo fornisce una soluzione per l'errore che si verifica durante la distribuzione durante l'aggiornamento a una versione che supporta PHP 8.1.
exl-id: bdc4a355-4f2b-49a7-9c5d-63c950f7ca30
feature: Deploy, Observability
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---

# Errore durante la distribuzione durante l’aggiornamento alla versione che supporta PHP 8.1

Questo articolo fornisce una soluzione per l&#39;errore che si verifica durante la distribuzione durante l&#39;aggiornamento a una versione che supporta PHP 8.1.

## Prodotti e versioni interessati

* Adobe Commerce sull’infrastruttura cloud 2.4.4. e versioni successive

* Estensione o tecnologia (Fastly, New Relic, ecc.) versione PHP 8.1

## Problema

Durante la distribuzione, durante l&#39;aggiornamento a una versione che supporta PHP 8.1, si verifica l&#39;errore seguente.

```PHP
{{E: Error parsing configuration files:

applications: Uncaught exception: The "json" extension is not supported for php:8.1
at <script>:109:12
throw("The \"" + unsupported_extensions[0] + "\" extension is not supported for " + service.type);
^
E: Error: Invalid configuration files, aborting build}}
```

## Causa

PHP 8.1 include già il supporto JSON e non richiede che l’estensione venga installata separatamente.

## Soluzione

Rimuovi JSON da **Runtime** > **Estensioni** sezione in `.magento.app.yaml` e la ridistribuzione.

## Lettura correlata

[applicazione PHP](https://devdocs.magento.com/cloud/project/magento-app-php-application.html) nella documentazione per gli sviluppatori.
