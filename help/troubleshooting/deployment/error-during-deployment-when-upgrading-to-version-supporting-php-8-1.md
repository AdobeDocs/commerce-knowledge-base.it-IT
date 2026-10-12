---
title: Errore durante la distribuzione durante l’aggiornamento alla versione che supporta PHP 8.1
description: Questo articolo fornisce una soluzione per l'errore che si verifica durante la distribuzione durante l'aggiornamento a una versione che supporta PHP 8.1.
exl-id: bdc4a355-4f2b-49a7-9c5d-63c950f7ca30
feature: Deploy, Observability
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: 4239b8a6-e74f-567d-a7a5-b98b9ead0ea4
    internal-label: Observability
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '148'
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

Rimuovi JSON dalla sezione **Runtime** > **Estensioni** in `.magento.app.yaml` e ridistribuiscilo.

## Lettura correlata

[applicazione PHP](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/configure/app/php-settings) nella documentazione per gli sviluppatori.
