---
title: 'PWA Studio: errori di convalida durante l’esecuzione della modalità sviluppatore'
description: In questo argomento viene illustrata una soluzione che consente di individuare i casi in cui si verificano errori di convalida durante l’esecuzione della modalità sviluppatore in Progressive Web App (PWA) Studio per Adobe Commerce a causa della mancata creazione del concetto di "venia" (Venia è una vetrina PWA). file di ambiente. Questo file conterrà le variabili per l’ambiente di sviluppo locale.
exl-id: 97d042ef-88e6-4eda-a834-2cff4de276e2
feature: Configuration
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%
---
# PWA Studio: errori di convalida durante l’esecuzione della modalità sviluppatore

In questo argomento viene illustrata una soluzione che consente di individuare i casi in cui si verificano errori di convalida durante l’esecuzione della modalità sviluppatore in Progressive Web App (PWA) Studio per Adobe Commerce a causa della mancata creazione del concetto di &quot;venia&quot; (Venia è una vetrina PWA). file di ambiente. Questo file conterrà le variabili per l’ambiente di sviluppo locale.

## Prodotti e versioni interessati

* PWA Studio per Adobe Commerce

## Problema

<u>Passaggio da riprodurre</u>:

* Eseguire la modalità sviluppatore in PWA Studio for Adobe Commerce.

<u>Risultato previsto</u>:

* Il server PWA Studio viene avviato normalmente.

<u>Risultato effettivo</u>:

* Vengono visualizzati errori di convalida simili ai seguenti:

```
    ⓧ  Missing required environment variables:         MAGENTO_BACKEND_URL: Connect to an instance of Adobe Commerce 2.3 by specifying its public domain name. (eg.         "https://master-7rqtwti-mfwmkrjfqvbjk.us-4.magentosite.cloud/")      ⚠  No .env file in ./packages/venia-concept. Autogenerate a .env file by running the command 'buildpack         create-env-file ./packages/venia-concept'.
```

## Causa

Manca il file delle variabili di ambiente per l’ambiente di sviluppo locale. Il file generato dal comando seguente conterrà le variabili per l’ambiente di sviluppo locale.

## Soluzione

Assicurarsi di eseguire il comando

```
npx @magento/pwa-buildpack create-env-file packages/venia-concept
```

nella directory principale per generare il file che conterrà le variabili per l’ambiente di sviluppo locale.

## Lettura correlata

* [Documentazione di PWA Studio per Adobe Commerce](https://developer.adobe.com/commerce/pwa-studio/)
* [Venia Storefront (concetto)](https://developer.adobe.com/commerce/pwa-studio/guides/packages/venia/)
