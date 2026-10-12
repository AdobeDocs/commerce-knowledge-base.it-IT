---
title: I profili cliente non vengono visualizzati in Experience Platform
description: In questo articolo vengono illustrati i passaggi per la risoluzione dei problemi se i dati del profilo cliente non vengono visualizzati in Experience Platform quando si utilizza l'estensione [!DNL Data Connection].
feature: Personalization, Integration, Configuration
role: Admin, Developer
exl-id: 4f12b032-0bee-47da-927a-8d4c2d8b8276
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: f37757d8-3174-5335-b977-1161792f965d
    internal-label: Personalization
  - id: cc04bd17-78d5-5120-8c3d-1b8a57e49280
    internal-label: Integration
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '556'
ht-degree: 0%
---
# I profili cliente non vengono visualizzati in Experience Platform

Questo articolo fornisce passaggi per la risoluzione dei problemi se i dati del profilo cliente non vengono visualizzati in Experience Platform quando si utilizza l’estensione Data Connection.

## Prodotti e versioni interessati

* Adobe Commerce 2.4.x con estensione [!DNL Data Connection] installata

## Problema

Hai installato e configurato l&#39;estensione [[!DNL Data Connection]](https://experienceleague.adobe.com/it/docs/commerce-merchant-services/data-connection/overview) e hai abilitato i dati del profilo cliente da inviare ad Experience Platform, ma tali dati di profilo non sono visualizzati in Experience Platform.

## Soluzione

Se le informazioni sul profilo cliente non sono visualizzate in Experience Platform, verifica quanto segue:

### Verificare che sia installata la versione più recente di [!DNL Data Connection]

Verificare di aver installato la versione più recente dell&#39;estensione `experience-platform-connector`.

Consulta le [[!DNL Data Connection] note sulla versione dell&#39;estensione](https://experienceleague.adobe.com/it/docs/commerce-merchant-services/data-connection/release-notes) per informazioni sull&#39;ultima versione.

>[!NOTE]
>
>La versione più recente dell&#39;estensione [!DNL Data Connection] include il modulo `customers-connector`, responsabile dell&#39;invio dei dati del profilo ad Experience Platform. La versione del modulo `customers-connector` deve essere `1.2.0` o successiva.

### Conferma la configurazione del modulo del connettore clienti

Conferma che il modulo `customers-connector` sia configurato in base allo scenario di installazione.

#### Adobe Commerce sull’infrastruttura cloud

1. Abilita la variabile globale `ENABLE_EVENTING` in `.magento.env.yaml`. [Ulteriori informazioni](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-global).

   ```bash
       stage:
           global:
               ENABLE_EVENTING: true
   ```

1. Esegui il commit e invia i file aggiornati all’ambiente Cloud. Al termine della distribuzione, abilita l’invio di eventi con il seguente comando:

   ```bash
       bin/magento config:set adobe_io_events/eventing/enabled 1
   ```

#### Installazione on-premise di Adobe Commerce

Esegui i seguenti comandi per abilitare la generazione del codice e gli eventi Adobe Commerce:

```bash
   bin/magento events:generate:module
   bin/magento module:enable Magento_AdobeCommerceEvents
   bin/magento setup:upgrade
   bin/magento setup:di:compile
   bin/magento config:set adobe_io_events/eventing/enabled 1
```

### Conferma di aver abilitato l’acquisizione e l’invio dei dati del profilo ad Experience Platform

In Amministrazione Commerce, accertati che siano impostati i seguenti campi:

* In **[!UICONTROL System]** > **[!UICONTROL Services]** > **[!UICONTROL Data Connection]**, verificare che le caselle di controllo [!UICONTROL Back office events] e [!UICONTROL Customer profiles] siano abilitate.
* Verificare che il campo *[!UICONTROL Profile Dataset ID]* sia corretto e che sia un set di dati diverso da quello attualmente utilizzato per i dati di eventi comportamentali e di back-office.

### Verifica se gli eventi vengono indirizzati alla gestione temporanea o alla produzione

1. Esegui il comando seguente per visualizzare l’ambiente Adobe Developer corrente:

   ```bash
   Copy code
   bin/magento config:show
   adobe_io_events/integration/adobe_io_environment
   ```

1. Se l&#39;ambiente è impostato su *[!UICONTROL Stage]*, modificarlo in *[!UICONTROL Production]* con il comando seguente:

   ```bash
   Copy code
   bin/magento config:set adobe_io_events/integration/adobe_io_environment
   production
   ```

### Tabella SaaS dati evento query

Connetti ed esegui la seguente query [!DNL SQL] per verificare che i record del profilo cliente siano visualizzati nel
Tabella `event_data_saas` e nessun errore:

```sql
Copy code
select * from event_data_saas;
```

### Gestire gli errori di pubblicazione degli eventi

1. Se riscontri il seguente errore, accertati che i tasti del connettore SaaS sandbox e di produzione siano corretti:

   ```css
   Copy code
   2024-06-07 14:37:57 | 2024-06-07 14:38:03 | 1 | 0 | Event publishing
   failed: Error code: 403; reason: Forbidden { "error": { "code":
   "Forbidden", "message": "Client ID is invalid", "details": {
   "error_code": "403003" } } }
   ```

1. Vai alla pagina *[!UICONTROL Commerce Services Connector]* nell&#39;amministratore e assicurati che le chiavi [!UICONTROL sandbox/production] specificate siano configurate correttamente. Verificare inoltre che le impostazioni dell&#39;account Commerce [!UICONTROL sandbox/production] corrispondano a quelle visualizzate in [!UICONTROL Commerce Services Connector]. Ulteriori informazioni [su](https://experienceleague.adobe.com/it/docs/commerce-merchant-services/user-guides/integration-services/saas#apikey).

### Controlla se l’ID servizio si trova nel inserisco nell&#39;elenco Consentiti di e conferma con il supporto di Adobe Commerce

1. Verificare che il [!UICONTROL Commerce Services Connector] `serviceId` sia visualizzato nel inserisco nell&#39;elenco Consentiti di in Adobe Commerce.
1. Contatta il [supporto Adobe Commerce](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) per confermare lo stato di inserita nell&#39;elenco Consentiti di

## Lettura correlata

* Estensione [[!DNL Data Connection]](https://experienceleague.adobe.com/it/docs/commerce-merchant-services/data-connection/overview) nella guida utente di Commerce Services
* [Best practice per la modifica delle tabelle del database](https://experienceleague.adobe.com/it/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) nel playbook di implementazione di Commerce
