---
title: "PWA Studi: errori di convalida durante l’esecuzione della modalità sviluppatore"
description: In questo argomento viene illustrata una soluzione che consente di individuare i casi in cui si verificano errori di convalida durante l’esecuzione della modalità sviluppatore in Progressive Web App (PWA) Studio per Adobe Commerce a causa della mancata creazione del concetto di "venia" (Venia è una vetrina PWA). file di ambiente. Questo file conterrà le variabili per l’ambiente di sviluppo locale.
exl-id: 97d042ef-88e6-4eda-a834-2cff4de276e2
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# PWA Studi: errori di convalida durante l’esecuzione della modalità sviluppatore

In questo argomento viene illustrata una soluzione che consente di individuare i casi in cui si verificano errori di convalida durante l’esecuzione della modalità sviluppatore in Progressive Web App (PWA) Studio per Adobe Commerce a causa della mancata creazione del concetto di &quot;venia&quot; (Venia è una vetrina PWA). file di ambiente. Questo file conterrà le variabili per l’ambiente di sviluppo locale.

## Prodotti e versioni interessati

* PWA Studi per Adobe Commerce

## Problema

<u>Passaggio da riprodurre</u>:

* Esegui modalità sviluppatore in PWA Studi per Adobe Commerce.

<u>Risultato previsto</u>:

* Il server PWA Studi viene avviato normalmente.

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

* [Documentazione di PWA Studi per Adobe Commerce](https://magento.github.io/pwa-studio/)
* [Venia Storefront (concetto)](https://magento.github.io/pwa-studio/venia-pwa-concept/)
