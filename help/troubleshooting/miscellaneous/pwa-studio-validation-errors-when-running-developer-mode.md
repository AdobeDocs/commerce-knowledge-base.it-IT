---
title: 'PWA Studio: errori di convalida durante l’esecuzione della modalità sviluppatore'
description: In questo argomento viene illustrata una soluzione per i casi in cui si verificano errori di convalida durante l’esecuzione della modalità sviluppatore in Progressive Web App (PWA) Studio per Adobe Commerce a causa della mancata creazione del file di ambiente venia-concept (Venia è una vetrina PWA). Questo file conterrà le variabili per l’ambiente di sviluppo locale.
exl-id: 97d042ef-88e6-4eda-a834-2cff4de276e2
feature: Configuration
role: Developer
source-git-commit: 9d32a5971341ed8dc46e0932c10eaac4d17ec299
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# PWA Studio: errori di convalida durante l’esecuzione della modalità sviluppatore

In questo argomento viene illustrata una soluzione per i casi in cui si verificano errori di convalida durante l’esecuzione della modalità sviluppatore in Progressive Web App (PWA) Studio per Adobe Commerce a causa della mancata creazione del file di ambiente venia-concept (Venia è una vetrina PWA). Questo file conterrà le variabili per l’ambiente di sviluppo locale.

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
* [Venia Storefront (Concetto)](https://developer.adobe.com/commerce/pwa-studio/guides/packages/venia/)
