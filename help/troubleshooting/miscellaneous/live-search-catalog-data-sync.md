---
title: Catalogo Live Search non sincronizzato
description: Questo articolo fornisce soluzioni per il problema di Adobe Commerce in cui i dati del catalogo non vengono sincronizzati correttamente quando si utilizza l’estensione Live Search.
exl-id: cd2e602f-b2c7-4ecf-874f-ec5f99ae1900
feature: Catalog Management, Search
role: Developer
source-git-commit: 5911b436fdcc08e695fb14d35784287945593815
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 0%

---

# Catalogo Live Search non sincronizzato

Questo articolo fornisce soluzioni per il problema di Adobe Commerce in cui i dati del catalogo non vengono sincronizzati correttamente quando si utilizza l’estensione Live Search.

## Prodotti e versioni interessati

* Adobe Commerce 2.4.x con estensione Live Search installata

## Problema

I dati del catalogo non vengono sincronizzati correttamente oppure è stato aggiunto un nuovo prodotto che non viene visualizzato nei risultati di ricerca. In `var/log/exception.log` è inoltre possibile che venga visualizzato il seguente errore:

`Magento_LiveSearch: An error occurred in search backend. {"result":{"errors":[{"message":"Exception while fetching data (/productSearch) : No index was found for this request"}]}}`

>[!NOTE]
>
>I nomi di tabella `catalog_data_exporter_products` e `catalog_data_exporter_product_attributes` sono ora denominati `cde_products_feed` e `cde_product_attributes_feed` a partire dalla versione 4.2.1 di [!DNL Live Search]. Per i commercianti con versioni precedenti alla 4.2.1, cerca i dati nei vecchi nomi di tabella, `catalog_data_exporter_products` e `catalog_data_exporter_product_attributes`.

<u>Passaggi da riprodurre</u>

1. Configura e connetti Live Search per la tua istanza di Adobe Commerce come descritto in [Installare Live Search > Configurare le chiavi API](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#configure-api-keys) nella documentazione utente.
1. Dopo 30 minuti, verificare i dati del catalogo esportati come descritto in [Installa Live Search > Verifica esportazione](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#verify-export) nella documentazione utente.
1. Dopo 30 minuti, verifica la connessione come descritto in [Installa Live Search > Verifica la connessione](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#test-connection) nella documentazione utente.

Oppure

1. Aggiungi un nuovo prodotto al catalogo.
1. Prova a eseguire una query di ricerca utilizzando il nome del prodotto o altri attributi ricercabili dopo 15-20 minuti dall’esecuzione di Magento indexer + cron per sincronizzare i dati con il servizio back-end.

<u>Risultato previsto</u>

* È possibile verificare i dati del catalogo esportati
* Connessione riuscita
* Il nuovo prodotto viene visualizzato nei risultati di ricerca.

<u>Risultato effettivo</u>

Impossibile verificare il catalogo esportato e/o stabilire la connessione perché la chiave API è stata modificata.

## Soluzione

Puoi provare a risolvere diversi problemi di sincronizzazione del catalogo.

### Attendi l&#39;applicazione delle modifiche

Una volta effettuata la configurazione e la connessione, la creazione dell’indice in ES (Elasticsearch) e la restituzione dei risultati della ricerca possono richiedere oltre 30 minuti. I successivi aggiornamenti una tantum dei prodotti dovrebbero essere indicizzati entro pochi minuti.

### Sincronizzare i dati di prodotto per uno SKU specifico

Se i dati di prodotto non vengono sincronizzati correttamente per una SKU specifica, effettua le seguenti operazioni:

1. Utilizzare la seguente query [!DNL SQL] e verificare di disporre dei dati previsti nella colonna `feed_data`. Prendere inoltre nota del timestamp `modified_at`.

   ```sql
   SELECT * FROM cde_products_feed WHERE json_extract(feed_data, '$.sku') = '<your_sku>' AND json_extract(feed_data, '$.storeViewCode') = '<your_ store_view_code>';
   ```

   Ad esempio:

   ```sql
   SELECT * FROM cde_products_feed WHERE json_extract(feed_data, '$.sku') = '24-MB04' AND json_extract(feed_data, '$.storeViewCode') = 'default';
   ```

1. Se non vengono visualizzati i dati corretti, provare a reindicizzare utilizzando il comando seguente ed eseguire nuovamente la query [!DNL SQL] nel passaggio 1 per verificare i dati:

   ```bash
   bin/magento indexer:reindex cde_products_feed
   ```

1. Se i dati corretti non vengono ancora visualizzati, [creare un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Controlla la marca temporale dell’ultima esportazione del prodotto

1. Se vengono visualizzati i dati corretti in `cde_products_feed`, utilizzare la seguente query [!DNL SQL] per verificare la marca temporale dell&#39;ultima esportazione. Deve essere dopo la marca temporale `modified_at`:

   ```sql
   select * from scopes_website_data_exporter;
   ```

1. Se il timestamp è meno recente, puoi attendere la successiva esecuzione del cron o attivarlo autonomamente utilizzando il seguente comando:

   ```bash
   bin/magento cron:run --group=saas_data_exporter
   ```

1. Attendere `<>` (tempo per aggiornamenti incrementali). Se i dati non vengono ancora visualizzati, [crea un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Sincronizza codice attributo specifico

Se i dati dell’attributo del prodotto non vengono sincronizzati correttamente per un codice di attributo specifico, effettua le seguenti operazioni:

1. Utilizzare la seguente query [!DNL SQL] e verificare di disporre dei dati previsti nella colonna `feed_data`. Prendere inoltre nota del timestamp `modified_at`.

   ```sql
   select * from cde_product_attributes_feed where json_extract(feed_data, '$.attributeCode') = '<your_attribute_code>' and store_view_code = '<your_ store_view_code>';
   ```

1. Se non vengono visualizzati i dati corretti, utilizzare il comando seguente per reindicizzare ed eseguire nuovamente la query [!DNL SQL] nel passaggio 1 per verificare i dati.

   ```bash
   bin/magento indexer:reindex cde_product_attributes_feed
   ```

1. Se i dati corretti non vengono ancora visualizzati, [creare un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Verifica la marca temporale dell’ultima esportazione dell’attributo del prodotto

Se vengono visualizzati i dati corretti in `cde_product_attributes_feed`:

1. Utilizzare la seguente query [!DNL SQL] per verificare la marca temporale dell&#39;ultima esportazione. Deve essere dopo la marca temporale `modified_at`.

   ```sql
   select * from scopes_website_data_exporter;
   ```

1. Se il timestamp è meno recente, puoi attendere la successiva esecuzione del cron o attivarlo autonomamente utilizzando il seguente comando:

   ```bash
   bin/magento cron:run --group=saas_data_exporter
   ```

1. Attendere 15-20 minuti (tempo per gli aggiornamenti incrementali). Se i dati non vengono ancora visualizzati, [crea un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Sincronizza dopo la modifica della configurazione API

(Problema noto) Se hai modificato la configurazione API, che comporta una modifica nell’ID dello spazio dati e riscontra che le modifiche apportate al catalogo non vengono più sincronizzate, esegui i seguenti comandi per risincronizzare i feed:

```
bin/magento saas:resync --feed productattributes --cleanup-feed
bin/magento saas:resync --feed products --cleanup-feed
bin/magento saas:resync --feed scopesCustomerGroup --cleanup-feed
bin/magento saas:resync --feed scopesWebsite --cleanup-feed
bin/magento saas:resync --feed prices --cleanup-feed
bin/magento saas:resync --feed productOverrides --cleanup-feed
bin/magento saas:resync --feed variants --cleanup-feed
bin/magento saas:resync --feed categories --cleanup-feed
bin/magento saas:resync --feed categoryPermissions --cleanup-feed
```

[Invia una richiesta di supporto](https://experienceleague.adobe.com/home?support-tab=home#support) per richiedere la reindicizzazione dell&#39;indice Live Search. Nella descrizione del problema, includi lo spazio dati/l&#39;ID ambiente trovato nel pannello di amministrazione in **[!UICONTROL System]** > **[!UICONTROL Services]** > **[!UICONTROL Commerce Services Connector]**.

>[!IMPORTANT]
>L&#39;utilizzo dell&#39;opzione `--cleanup-feed` in altri casi può causare la perdita di dati e problemi di sincronizzazione dei dati.  Utilizzalo solo quando hai un nuovo ambiente vuoto, dopo che il team di Adobe ha completato un&#39;operazione di pulizia dello spazio dati o quando esegui il comando `saas:resync` con l&#39;opzione [—dry-run](https://experienceleague.adobe.com/en/docs/commerce/saas-data-export/data-export-cli-commands#--dry-run). L&#39;utilizzo dell&#39;opzione `--cleanup-feed` in altri casi può causare la perdita di dati e problemi di sincronizzazione dei dati.

## Lettura correlata

* [Onboarding Live Search](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/onboarding-overview.html) nella documentazione utente
* [Esaminare i registri e risolvere i problemi relativi all&#39;esportazione e alla sincronizzazione dei dati Adobe Commerce SaaS](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/troubleshooting-logging) nella Guida all&#39;esportazione dei dati Adobe Commerce SaaS
* [Best practice per la modifica delle tabelle del database](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) nel playbook di implementazione di Commerce
