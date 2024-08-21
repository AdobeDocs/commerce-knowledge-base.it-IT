---
title: Catalogo Live Search non sincronizzato
description: Questo articolo fornisce soluzioni per il problema di Adobe Commerce in cui i dati del catalogo non vengono sincronizzati correttamente quando si utilizza l’estensione Live Search.
exl-id: cd2e602f-b2c7-4ecf-874f-ec5f99ae1900
feature: Catalog Management, Search
role: Developer
source-git-commit: ab39a21ca325cdad30debf89a1cff660bf5925e5
workflow-type: tm+mt
source-wordcount: '682'
ht-degree: 0%

---

# Catalogo Live Search non sincronizzato

Questo articolo fornisce soluzioni per il problema di Adobe Commerce in cui i dati del catalogo non vengono sincronizzati correttamente quando si utilizza l’estensione Live Search.

## Prodotti e versioni interessati

* Adobe Commerce 2.4.x con estensione Live Search installata

## Problema

I dati del catalogo non vengono sincronizzati correttamente oppure è stato aggiunto un nuovo prodotto che non viene visualizzato nei risultati di ricerca.

<u>Passaggi da riprodurre</u>

1. Configura e connetti Live Search per la tua istanza di Adobe Commerce come descritto in [Installare Live Search > Configurare le chiavi API](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#configure-api-keys) nella documentazione utente.
1. Dopo 30 minuti, verificare i dati del catalogo esportati come descritto in [Installa Live Search > Verifica esportazione](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#verify-export) nella documentazione utente.
1. Dopo 30 minuti, verifica la connessione come descritto in [Installa Live Search > Verifica la connessione](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#test-connection) nella documentazione utente.

Oppure

1. Aggiungi un nuovo prodotto al catalogo.
1. Prova a eseguire una query di ricerca utilizzando il nome del prodotto o altri attributi ricercabili dopo 15-20 minuti dall’esecuzione dell’indicizzatore del Magento temporale + cron per sincronizzare i dati con il servizio back-end.

<u>Risultato previsto</u>

* È possibile verificare i dati del catalogo esportati
* Connessione riuscita
* Il nuovo prodotto viene visualizzato nei risultati di ricerca.

<u>Risultato effettivo</u>

Impossibile verificare il catalogo esportato e/o stabilire la connessione perché la chiave API è stata modificata.

## Soluzione

Puoi provare a risolvere diversi problemi di sincronizzazione del catalogo.

### Attendi l&#39;applicazione delle modifiche

Una volta effettuata la configurazione e la connessione, possono essere necessari più di 30 minuti per la creazione dell’indice in ES (Elasticsearch) e la restituzione dei risultati della ricerca. I successivi aggiornamenti una tantum dei prodotti dovrebbero essere indicizzati entro pochi minuti.

### Sincronizzare i dati di prodotto per uno SKU specifico

Se i dati di prodotto non vengono sincronizzati correttamente per una SKU specifica, effettua le seguenti operazioni:

1. Utilizzare la seguente query SQL e verificare di disporre dei dati previsti nella colonna `feed_data`. Prendere inoltre nota del timestamp `modified_at`.

   ```sql
   select * from catalog_data_exporter_products where sku = '<your_sku>' and store_view_code = '<your_ store_view_code>';
   ```

1. Se non vengono visualizzati i dati corretti, provare a reindicizzare utilizzando il comando seguente ed eseguire nuovamente la query SQL al passaggio 1 per verificare i dati:

   ```bash
   bin/magento indexer:reindex catalog_data_exporter_products
   ```

1. Se i dati corretti non vengono ancora visualizzati, [creare un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Controlla la marca temporale dell’ultima esportazione del prodotto

1. Se vengono visualizzati i dati corretti in `catalog_data_exporter_products`, utilizzare la query SQL seguente per verificare la marca temporale dell&#39;ultima esportazione. Deve essere dopo la marca temporale `modified_at`:

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

1. Utilizzare la seguente query SQL e verificare di disporre dei dati previsti nella colonna `feed_data`. Prendere inoltre nota del timestamp `modified_at`.

   ```sql
   select * from catalog_data_exporter_product_attributes where json_extract(feed_data, '$.attributeCode') = '<your_attribute_code>' and store_view_code = '<your_ store_view_code>';
   ```

1. Se i dati corretti non vengono visualizzati, utilizzare il comando seguente per reindicizzare ed eseguire nuovamente la query SQL nel passaggio 1 per verificare i dati.

   ```bash
   bin/magento indexer:reindex catalog_data_exporter_product_attributes
   ```

1. Se i dati corretti non vengono ancora visualizzati, [creare un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Verifica la marca temporale dell’ultima esportazione dell’attributo del prodotto

Se vengono visualizzati i dati corretti in `catalog_data_exporter_product_attributes`:

1. Utilizza la seguente query SQL per verificare la marca temporale dell’ultima esportazione. Deve essere dopo la marca temporale `modified_at`.

   ```sql
   select * from scopes_website_data_exporter;
   ```

1. Se il timestamp è meno recente, puoi attendere la successiva esecuzione del cron o attivarlo autonomamente utilizzando il seguente comando:

   ```bash
   bin/magento cron:run --group=saas_data_exporter
   ```

1. Attendere 15-20 minuti (tempo per gli aggiornamenti incrementali). Se i dati non vengono ancora visualizzati, [crea un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Sincronizza dopo la modifica della configurazione API

(Problema noto) Se hai modificato la configurazione API, che comporta una modifica nell’ID dello spazio dati e riscontra che le modifiche al catalogo non vengono più sincronizzate, esegui i seguenti comandi:

```bash
bin/magento saas:resync --feed products
bin/magento saas:resync --feed productattributes
```

## Lettura correlata

* Consulta [Onboard Live Search](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/onboarding-overview.html) nella documentazione utente.
* Consulta [Esaminare i registri e risolvere i problemi relativi all&#39;esportazione e alla sincronizzazione dei dati Adobe Commerce SaaS](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/troubleshooting-logging) nella Guida all&#39;esportazione dei dati Adobe Commerce SaaS.
