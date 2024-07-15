---
title: Risoluzione dei problemi del modulo Product Recommendations in Adobe Commerce
description: In questo articolo vengono illustrati suggerimenti per la risoluzione dei problemi relativi al
exl-id: 431ee31e-eb5b-400c-9c99-cc86613453d7
feature: Cache, Compliance, Extensions, Marketing Tools, Personalization, Products, Recommendations
role: Developer
source-git-commit: b20ad74194bacb09116131f4a8da1006da75738a
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# Risoluzione dei problemi del modulo Product Recommendations in Adobe Commerce

In questo articolo vengono illustrati suggerimenti per la risoluzione dei problemi relativi al

```php
magento/product-recommendations
```

modulo e relativa dipendenza

```php
saas-export
```

perché è necessario che entrambi i moduli funzionino per utilizzare lo strumento Product Recommendations in Adobe Commerce.

## Prodotti e versioni interessati

* Adobe Commerce 2.4.4 - 2.4.7

## Risoluzione dei problemi del modulo di consigli sui prodotti

Se hai configurato il

```php
magento/product-recommendations
```

modulo corretto (controllare [Recommendations di prodotto - Installare e configurare Recommendations](https://devdocs.magento.com/recommendations/install-configure.html) nella documentazione per gli sviluppatori.), ma non vengono visualizzati consigli, provare a eseguire le operazioni seguenti:

* È possibile che il modulo non abbia avuto abbastanza tempo per raccogliere i dati comportamentali. Consenti al sistema di funzionare per 24 ore in modo che possa iniziare a raccogliere dati. Prendi in considerazione la distribuzione di un tipo di consiglio che non richiede dati comportamentali, ad esempio &quot;Altri argomenti correlati&quot;.

* Se non visualizzi i consigli configurati, è possibile che non siano ancora disponibili dati sufficienti per creare consigli per l’utente.

* Verifica che lo spazio dati SaaS o la chiave API siano validi. Se ricevi un errore dopo aver specificato lo spazio dati SaaS o la chiave API durante l&#39;inizializzazione dei consigli di prodotto, verifica di aver immesso correttamente lo spazio dati e la chiave API [SaaS](https://docs.magento.com/user-guide/configuration/services/saas.html) (nella nostra guida utente). Per garantire che MageID e la chiave API siano collegati, l’utente proprietario di MageID, in genere l’utente proprietario della licenza Adobe Commerce, deve essere lo stesso utente che genera la chiave API. Se devi modificare l&#39;ID immagine utilizzato, [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

>[!NOTE]
>
>Se la modalità di restrizione dei cookie [1} (nella guida utente) è abilitata, Adobe Commerce non raccoglie i dati comportamentali fino al consenso dell&#39;acquirente. ](https://docs.magento.com/m2/ce/user_guide/stores/compliance-cookie-restriction-mode.html) Se la modalità di restrizione dei cookie è disabilitata, Adobe Commerce raccoglie i dati comportamentali per impostazione predefinita.

## Modulo esportazione SaaS catalogo

Per problemi relativi all’esportazione SaaS del catalogo (

```php
saas-export
```

):

1. Conferma l&#39;esecuzione dei processi [cron](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-cron.html) (nella documentazione per gli sviluppatori).
1. Conferma l&#39;esecuzione degli [indicizzatori](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-index.html) (nella documentazione per gli sviluppatori) e    ```php    Product Feed    ```    indicizzatore impostato su    ```php    Update by Schedule    ```    .
1. Conferma l’attivazione dei moduli. Il    ```php    saas-export    ```    metapackage installa i seguenti moduli, che devono essere tutti abilitati:    ```php    "magento/module-catalog-data-exporter"      "magento/module-catalog-inventory-data-exporter"      "magento/module-catalog-url-rewrite-data-exporter"      "magento/module-configurable-product-data-exporter"      "magento/module-data-exporter"      "magento/module-saas-catalog"    ```
1. Controlla i [registri](https://devdocs.magento.com/guides/v2.3/config-guide/cli/logging.html) (nella documentazione per gli sviluppatori). Assicurati che non vi siano errori associati ai moduli di cui sopra.
1. Aggiorna cache di configurazione. Vai a **Sistema** > **Strumenti** > **Gestione cache** e cancella la cache di configurazione.
1. Verifica che siano presenti dati in    ```php    catalog_data_exporter_products    ```    tabella di database.

## Eventi

[Eventi consigli](https://devdocs.magento.com/recommendations/verify.html), nella documentazione per gli sviluppatori, descrive gli eventi comportamentali inviati ad Adobe Commerce.

## Lettura correlata

* [Product Recommendations - Panoramica](https://devdocs.magento.com/recommendations/product-recs.html) nella documentazione per gli sviluppatori
* [Product Recommendations - Installa e configura Recommendations](https://devdocs.magento.com/recommendations/install-configure.html) nella documentazione per gli sviluppatori
* [Marketing - Product Recommendations](https://docs.magento.com/m2/ee/user_guide/marketing/product-recommendations.html) nella guida utente
* [Creare Recommendations](https://docs.magento.com/m2/ee/user_guide/marketing/create-new-rec.html) nella guida utente
