---
title: I profili cliente non vengono visualizzati in Experience Platform
description: In questo articolo vengono illustrati i passaggi per la risoluzione dei problemi se i dati del profilo cliente non vengono visualizzati nell'Experience Platform quando si utilizza l'estensione  [!DNL Data Connection] .
feature: Personalization, Integration, Configuration
role: Admin, Developer
exl-id: 4f12b032-0bee-47da-927a-8d4c2d8b8276
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# I profili cliente non vengono visualizzati in Experience Platform

Questo articolo fornisce passaggi per la risoluzione dei problemi se i dati del profilo cliente non vengono visualizzati nell’Experience Platform quando si utilizza l’estensione Data Connection.

## Prodotti e versioni interessati

* Adobe Commerce 2.4.x con estensione [!DNL Data Connection] installata

## Problema

L&#39;estensione [[!DNL Data Connection]](https://experienceleague.adobe.com/it/docs/commerce-merchant-services/data-connection/overview) è stata installata e configurata e i dati del profilo cliente sono stati abilitati per l&#39;invio all&#39;Experience Platform, ma i dati del profilo non sono visualizzati nell&#39;Experience Platform.

## Soluzione

Se le informazioni sul profilo cliente non sono visualizzate nell’Experience Platform, verifica quanto segue:

### Verificare che sia installata la versione più recente di [!DNL Data Connection]

Verificare di aver installato la versione più recente dell&#39;estensione `experience-platform-connector`.

Consulta le [[!DNL Data Connection] note sulla versione dell&#39;estensione](https://experienceleague.adobe.com/it/docs/commerce-merchant-services/data-connection/release-notes) per informazioni sull&#39;ultima versione.

>[!NOTE]
>
>La versione più recente dell&#39;estensione [!DNL Data Connection] include il modulo `customers-connector`, responsabile dell&#39;invio dei dati del profilo all&#39;Experience Platform. La versione del modulo `customers-connector` deve essere `1.2.0` o successiva.

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

### Conferma di aver abilitato i dati del profilo da acquisire e inviare all’Experience Platform

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

1. Verificare che l&#39;elemento [!UICONTROL Commerce Services Connector] `serviceId` venga visualizzato nel elenco Consentiti di controllo in Adobe Commerce.
1. Contatta il [supporto Adobe Commerce](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) per confermare lo stato di inserita nell&#39;elenco Consentiti del.

## Lettura correlata

* Estensione [[!DNL Data Connection]](https://experienceleague.adobe.com/it/docs/commerce-merchant-services/data-connection/overview) nella guida utente di Commerce Services
* [Best practice per la modifica delle tabelle del database](https://experienceleague.adobe.com/it/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) nel playbook di implementazione di Commerce
