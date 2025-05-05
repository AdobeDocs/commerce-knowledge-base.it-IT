---
title: Risolvere i problemi relativi al modulo [!UICONTROL Product Recommendations] in Adobe Commerce
description: In questo articolo vengono forniti suggerimenti per la risoluzione dei problemi relativi al modulo [!UICONTROL Product Recommendations] in Adobe Commerce.
exl-id: 431ee31e-eb5b-400c-9c99-cc86613453d7
feature: Cache, Compliance, Extensions, Marketing Tools, Personalization, Products, Recommendations
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%

---

# Risolvere i problemi relativi al modulo [!UICONTROL Product Recommendations] in Adobe Commerce

In questo articolo vengono illustrati suggerimenti per la risoluzione dei problemi relativi al

```php
magento/product-recommendations
```

modulo e relativa dipendenza

```php
saas-export
```

perché è necessario che entrambi i moduli funzionino per utilizzare lo strumento [!UICONTROL Product Recommendations] in Adobe Commerce.

## Prodotti e versioni interessati

* Adobe Commerce 2.4.4 - 2.4.7

## Risoluzione dei problemi del modulo di consigli sui prodotti

Se hai configurato il

```php
magento/product-recommendations
```

modulo corretto (controllare [[!UICONTROL Product Recommendations - Install and Configure]](https://experienceleague.adobe.com/it/docs/commerce-merchant-services/product-recommendations/getting-started/install-configure) nella documentazione per gli sviluppatori). ma non si visualizzano consigli, provare a eseguire le operazioni seguenti:

* È possibile che il modulo non abbia avuto abbastanza tempo per raccogliere i dati comportamentali. Consenti al sistema di funzionare per 24 ore in modo che possa iniziare a raccogliere dati. Valuta la possibilità di distribuire un tipo di consiglio che non richiede dati comportamentali, ad esempio &quot;*Altri tipi simili*&quot;.

* Se non visualizzi i consigli configurati, è possibile che non siano ancora presenti dati sufficienti per creare consigli per l’utente.

* Verificare che lo spazio dati [!DNL SaaS] o la chiave [!DNL API] siano validi. Se ricevi un errore dopo aver specificato lo spazio dati [!DNL SaaS] o la chiave [!DNL API] durante l&#39;inizializzazione dei consigli di prodotto, verifica di aver immesso correttamente lo spazio dati [[!DNL SaaS] e la chiave  [!DNL API] 4&rbrace; (nella nostra guida utente). ](https://experienceleague.adobe.com/it/docs/commerce-admin/config/services/saas) Per assicurarsi che la chiave [!DNL MageID] e la chiave [!DNL API] siano collegate, l&#39;utente proprietario di [!DNL MageID], in genere l&#39;utente proprietario della licenza Adobe Commerce, deve essere lo stesso utente che genera la chiave [!DNL API]. Se è necessario modificare [!DNL MageID] utilizzato, [inviare un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

>[!NOTE]
>
>Se [**[!UICONTROL Cookie Restriction Mode]**](https://experienceleague.adobe.com/it/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law) (nella nostra guida utente) è *abilitato*, Adobe Commerce non raccoglie dati comportamentali fino al consenso dell&#39;acquirente. Se **[!UICONTROL Cookie Restriction Mode]**&#x200B;è *disabilitato*, Adobe Commerce raccoglie i dati comportamentali per impostazione predefinita.

## Modulo di esportazione [!DNL SaaS] catalogo

Per problemi relativi all&#39;esportazione del catalogo [!DNL SaaS] (

```php
saas-export
```

):

1. Conferma l&#39;esecuzione dei processi [[!DNL cron]](https://experienceleague.adobe.com/it/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) (nella documentazione per gli sviluppatori).
1. Verificare che [[!UICONTROL indexers]](https://experienceleague.adobe.com/it/docs/commerce-operations/configuration-guide/cli/manage-indexers) (nella documentazione per gli sviluppatori) sia in esecuzione e che    ```php    Product Feed    ```    [!UICONTROL indexer] è impostato su    ```php    Update by Schedule    ```    .
1. Verificare che i moduli siano *abilitati*. Il    ```php    saas-export    ```    metapackage installa i seguenti moduli, che devono essere tutti *abilitati*:    ```php    "magento/module-catalog-data-exporter"      "magento/module-catalog-inventory-data-exporter"      "magento/module-catalog-url-rewrite-data-exporter"      "magento/module-configurable-product-data-exporter"      "magento/module-data-exporter"      "magento/module-saas-catalog"    ```
1. Controlla i [registri](https://experienceleague.adobe.com/it/docs/commerce-operations/configuration-guide/cli/enable-logging) (nella documentazione per gli sviluppatori). Assicurati che non vi siano errori associati ai moduli di cui sopra.
1. Aggiorna [!UICONTROL Configuration cache]. Vai a **Sistema** > **Strumenti** > **Gestione cache** e cancella [!UICONTROL Configuration cache].
1. Verificare che siano presenti dati nella tabella del database `cde_products_products_feed`.

   >[!NOTE]
   >
   >Se la tabella non viene trovata, controllare la tabella `catalog_data_exporter_products`. Il nome della tabella è stato modificato nella versione 103.3.0 di [!DNL Data Export].

## Eventi

[Verifica raccolta eventi](https://experienceleague.adobe.com/it/docs/commerce-merchant-services/product-recommendations/getting-started/verify), nella documentazione per gli sviluppatori, descrive gli eventi comportamentali inviati ad Adobe Commerce.

## Lettura correlata

* [Product Recommendations Administrator Development](https://experienceleague.adobe.com/it/docs/commerce-merchant-services/product-recommendations/developer/development-overview) nella documentazione per gli sviluppatori
* [Introduzione a Recommendations](https://experienceleague.adobe.com/it/docs/commerce-merchant-services/product-recommendations/overview) nella Guida di Product Recommendations
* [Creazione di Recommendations](https://experienceleague.adobe.com/it/docs/commerce-merchant-services/product-recommendations/admin/create) nella Guida di Product Recommendations
* [Esaminare i registri e risolvere i problemi](https://experienceleague.adobe.com/it/docs/commerce-merchant-services/saas-data-export/troubleshooting-logging) nella Guida all&#39;esportazione dei dati di [!DNL SaaS]
* [[!DNL SaaS] Note sulla versione dell&#39;estensione per l&#39;esportazione dei dati](https://experienceleague.adobe.com/it/docs/commerce-merchant-services/saas-data-export/release-notes) nella Guida all&#39;esportazione dei dati di Adobe Commerce per i servizi [!DNL SaaS]
* [Best practice per la modifica delle tabelle del database](https://experienceleague.adobe.com/it/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) nel playbook di implementazione di Commerce

