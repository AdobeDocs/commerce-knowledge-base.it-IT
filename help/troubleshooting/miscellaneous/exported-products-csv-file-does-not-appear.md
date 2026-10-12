---
title: Il file .csv dei prodotti esportati non viene visualizzato
description: Questo articolo corregge il problema relativo al tentativo di esportare il tipo di entità desiderato in un file .csv in Commerce Admin, ma il file non viene visualizzato.
exl-id: 8e3bb65c-ea75-4af4-ad4b-4d94ab219bbb
feature: Cache, Data Import/Export, Products, Variables
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 601e4abe-d9bf-58de-a779-32ed6794dcbe
    internal-label: Data Import/Export
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: 8d0b446f-5b16-5a10-b272-01143504a11c
    internal-label: System
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: 2191e157-828a-5358-ad69-ebcaa8402915
    internal-label: Variables
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '709'
ht-degree: 0%
---
# Il file .csv dei prodotti esportati non viene visualizzato

Questo articolo fornisce una soluzione per il problema relativo all’esportazione del tipo di entità desiderato in un file .csv in Commerce Admin, causando la mancata visualizzazione del file.

## Prodotti e versioni interessati

* Adobe Commerce sull&#39;infrastruttura cloud, tutte le [versioni supportate](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problema

<u>Passaggi da riprodurre</u>

Prerequisiti: l&#39;opzione **Aggiungi chiave segreta agli URL** è impostata su *Sì*. L&#39;opzione è configurata in Amministrazione Commerce in **Archivi** > **Configurazione** > **Avanzate** > **Amministrazione** > **Sicurezza**.

1. In Amministrazione, passa a **Sistema** > **Trasferimento dati** > **Esporta**.

   ![magento_export_products_2.3.4.png](assets/magento_export_products_2.3.4.png)

1. Seleziona
   * **Tipo di entità**: l&#39;entità da esportare
   * **Formato file esportazione**: *CSV*
   * **Enclosure campo**: lasciare deselezionata.
1. Fai clic su **Continua**.
1. Viene visualizzato il seguente messaggio: *&quot;Il messaggio è stato aggiunto alla coda, attendi di ottenere il file a breve&quot;*.

<u>Risultato previsto</u>

Il file .csv contenente il tipo di entità desiderato esportato viene visualizzato nella griglia entro un paio di minuti.

<u>Risultato effettivo</u>

Il file .csv contenente il tipo di entità desiderato esportato non viene visualizzato nella griglia in 10 minuti o più.

## Causa

Si è verificato un problema noto con la funzionalità di esportazione nella versione 2.3.2 della parte dell’applicazione Adobe Commerce.

## Soluzione

Esistono due possibili soluzioni per il problema:

* Disattiva l’opzione Aggiungi chiave segreta all’URL.
* Eseguire il comando `bin/magento queue:consumers:start exportProcessor` manualmente e configurarlo per l&#39;esecuzione da parte di cron.

I dettagli di entrambe le opzioni sono riportati nei paragrafi seguenti.

### Disattiva l’opzione Aggiungi chiave segreta all’URL

1. In Amministrazione, passa a **Archivi** > **Configurazione** > **Avanzate** > **Amministrazione** > **Sicurezza**.
1. Imposta l&#39;opzione **Aggiungi chiave segreta agli URL** su *No.*
1. Fai clic su **Salva configurazione**.
1. Pulisci la cache in **Sistema** > **Strumenti** > **Gestione cache** o eseguendo `bin/magento cache:clean` o nell&#39;amministratore.

### Esegui il comando di esportazione manualmente e, facoltativamente, aggiungilo come processo cron

Per ottenere il file di esportazione, eseguire il comando `bin/magento queue:consumers:start exportProcessor`. Dopo aver eseguito questa operazione, il file deve essere visualizzato nella griglia.


Per aggiungere il processo come processo cron, è necessario aggiungere la variabile `CRON_CONSUMERS` al file `.magento.env.yaml`.

#### Aggiungi processo come processo cron (facoltativo)

1. Assicurati che il cron sia configurato e configurato. Per ulteriori informazioni, vedere [Configurare i processi cron](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html?lang=it).
1. Eseguire il comando seguente per restituire un elenco di consumer della coda di messaggi: `./bin/magento queue:consumers:list`
1. Aggiungere quanto segue al file `.magento.env.yaml` nella directory dell&#39;applicazione radice e includere i consumer che si desidera aggiungere. Ad esempio, ecco il consumatore necessario per l’elaborazione dell’esportazione:

   ```yaml
   stage:
       deploy:
           CRON_CONSUMERS_RUNNER:
               cron_run: true
               max_messages: 1000
               consumers:
                   - exportProcessor
   ```

   Quindi invia questo file aggiornato e ridistribuisci l’ambiente. Vedi anche [Aggiungere processi cron personalizzati al progetto](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html?lang=it#add-custom-cron-jobs-to-your-project) nella documentazione per gli sviluppatori.

>[!NOTE]
>
>Se non riesci a trovare il file `.magento.env.yaml` per il tuo ambiente e pensi che sia stato eliminato, devi creare un nuovo `.magento.env.yaml`. Inizialmente potrebbe essere vuoto, puoi aggiungere le informazioni in base alle esigenze. Consulta i seguenti articoli: [Configurare le variabili di ambiente per la distribuzione](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html?lang=it) e [Variabili di ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html?lang=it) nella documentazione per gli sviluppatori.

>[!TIP]
>
>[I file YAML](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html?lang=it) fanno distinzione tra maiuscole e minuscole e non consentono tabulazioni. Fai attenzione a utilizzare un rientro coerente in tutto il file .magento.env.yaml, altrimenti la configurazione potrebbe non funzionare come previsto. Gli esempi nella documentazione e nel file di esempio utilizzano il rientro a due spazi. Utilizza il comando di convalida degli strumenti ece per controllare la configurazione.

>[!NOTE]
>
>Nei progetti Pro di Adobe Commerce su infrastrutture cloud, la funzione [auto-crons](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html?lang=it#crontab) deve essere abilitata nell&#39;infrastruttura Adobe Commerce su cloud prima di poter aggiungere processi cron personalizzati agli ambienti di staging e produzione utilizzando `.magento.app.yaml`. Se questa funzionalità non è abilitata, [crea un ticket di supporto](https://experienceleague.adobe.com/it/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) per aggiungere il processo.

