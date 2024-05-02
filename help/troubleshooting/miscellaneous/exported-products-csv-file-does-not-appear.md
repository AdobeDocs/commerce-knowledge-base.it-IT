---
title: Il file .csv dei prodotti esportati non viene visualizzato
description: Questo articolo corregge il problema relativo al tentativo di esportazione di prodotti in un file .csv in Commerce Admin, ma il file non viene visualizzato.
exl-id: 8e3bb65c-ea75-4af4-ad4b-4d94ab219bbb
feature: Cache, Data Import/Export, Products, Variables
role: Developer
source-git-commit: 465eb89cf5c5169b0b459ab7e6bdcbd418781093
workflow-type: tm+mt
source-wordcount: '527'
ht-degree: 0%

---

# Il file .csv dei prodotti esportati non viene visualizzato

Questo articolo corregge il problema relativo al tentativo di esportazione di prodotti in un file .csv in Commerce Admin, ma il file non viene visualizzato.

## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud, tutto [versioni supportate](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problema

<u>Passaggi da riprodurre</u>

Prerequisiti: **Aggiungi chiave segreta agli URL** è impostata su *Sì*. L’opzione è configurata in Amministrazione Commerce in **Negozi** > **Configurazione** > **Avanzate** > **Amministratore** > **Sicurezza**.

1. In Admin, passa a **Sistema** > **Trasferimento dati** > **Esporta**.

   ![magento_export_products_2.3.4.png](assets/magento_export_products_2.3.4.png)

1. Seleziona
   * **Tipo di entità**: *Prodotti*
   * **Esporta formato file**: *CSV*
   * **Enclosure per campi**: lascia deselezionato.
1. Clic **Continua**.
1. Viene visualizzato il seguente messaggio: *&quot;Il messaggio viene aggiunto alla coda, attendi di ottenere il file a breve&quot;*.

<u>Risultato previsto</u>

Il file .csv con i prodotti esportati viene visualizzato nella griglia in pochi minuti.

<u>Risultato effettivo</u>

Il file .csv con i prodotti esportati non viene visualizzato nella griglia in 10 minuti o più.

## Causa

Si è verificato un problema noto con la funzionalità di esportazione nella versione 2.3.2 della parte dell’applicazione Adobe Commerce.

## Soluzione

Esistono due possibili soluzioni per il problema:

* Disattiva l’opzione Aggiungi chiave segreta all’URL.
* Esegui il `bin/magento queue:consumers:start exportProcessor` e configurarlo per essere eseguito da cron.

I dettagli di entrambe le opzioni sono riportati nei paragrafi seguenti.

### Disattiva l’opzione Aggiungi chiave segreta all’URL

1. In Admin, passa a **Negozi** > **Configurazione** > **Avanzate** > **Amministratore** > **Sicurezza**.
1. Imposta il **Aggiungi chiave segreta agli URL** opzione per *No.*
1. Clic **Salva configurazione**.
1. Pulisci cache in **Sistema** > **Strumenti** > **Gestione cache** o eseguendo    ```bash    bin/magento cache:clean``` o nell’Amministratore.

### Esegui il comando di esportazione manualmente e, facoltativamente, aggiungilo come processo cron

Per ottenere il file di esportazione, eseguire la `bin/magento queue:consumers:start exportProcessor` comando. Dopo aver eseguito questa operazione, il file deve essere visualizzato nella griglia.


Per aggiungere il processo come processo cron, è necessario aggiungere `CRON_CONSUMERS` variabile a `.magento.env.yaml` file.

#### Aggiungi processo come processo cron (facoltativo)

1. Assicurati che il cron sia configurato e configurato. Consulta [Imposta processi cron](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html) per i dettagli.
1. Esegui il comando seguente per restituire un elenco di consumer della coda di messaggi:     `./bin/magento queue:consumers:list`
1. Aggiungi quanto segue al tuo `.magento.env.yaml` nella directory principale dell&#39;applicazione e includere i consumer che si desidera aggiungere. Ad esempio, ecco il consumatore necessario per l’elaborazione dell’esportazione:

   ```yaml
   stage:
       deploy:
           CRON_CONSUMERS_RUNNER:
               cron_run: true
               max_messages: 1000
               consumers:
                   - exportProcessor
   ```

   Quindi invia questo file aggiornato e ridistribuisci l’ambiente. Riferimento anche [Aggiungi processi cron personalizzati al progetto](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#add-custom-cron-jobs-to-your-project) nella documentazione per gli sviluppatori.

>[!NOTE]
>
>Se non riesci a trovare `.magento.env.yaml` per il tuo ambiente e pensi che sia stato eliminato, devi creare un nuovo `.magento.env.yaml`. Inizialmente potrebbe essere vuoto, puoi aggiungere le informazioni in base alle esigenze. Fai riferimento ai seguenti articoli: [Configurare le variabili di ambiente per la distribuzione](/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) e [Variabili di ambiente](/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html) nella documentazione per gli sviluppatori.

>[!NOTE]
>
>Nei progetti Adobe Commerce su infrastruttura cloud Pro, il [funzione auto-crons](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html?lang=en#crontab) deve essere abilitato nell’infrastruttura cloud di Adobe Commerce per poter aggiungere processi cron personalizzati agli ambienti di staging e produzione tramite `.magento.app.yaml`. Se questa funzione non è abilitata, [creare un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), per aggiungere il lavoro.
