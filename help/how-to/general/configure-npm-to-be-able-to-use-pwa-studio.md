---
title: Configurare NPM per l'utilizzo di PWA Studi
description: '''[Progressive Web Apps (PWA) Studio](https://magento.github.io/pwa-studio/) è un nuovo progetto disponibile per Adobe Commerce su infrastruttura cloud 2.3.x o versione successiva. Per poter utilizzare e installare PWA Studi, è necessario impostare la versione di Gestione pacchetti NPM su 5.x o successiva per ottenere il supporto per Node.js 8.x. Questa operazione viene eseguita nella sezione "hooks:build" del file di configurazione `.magento.app.yaml`.’'
exl-id: 3854fc94-e8ad-45d8-bf3e-73462364220d
source-git-commit: 37ac9cca1f876a48092467aa38f2f2f013c83dd9
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Configurare NPM per l&#39;utilizzo di PWA Studi

[Progressive Web Apps (PWA) Studio](https://magento.github.io/pwa-studio/) è un nuovo progetto disponibile per Adobe Commerce su infrastruttura cloud 2.3.x o versione successiva. Per poter utilizzare e installare PWA Studi, è necessario impostare la versione di Gestione pacchetti NPM su 5.x o successiva per ottenere il supporto per Node.js 8.x. Questa operazione viene eseguita nel `hooks:build` sezione del `.magento.app.yaml` file di configurazione.

## Ambiente e tecnologie

* Adobe Commerce sull’infrastruttura cloud 2.3.X
* PWA per Adobe Commerce

## Imposta versione NPM: passaggi

Per impostare la versione NPM necessaria, specificarla nella `.magento.app.yaml` file di configurazione. Segui questi passaggi:

1. Nell’ambiente di sviluppo locale, individua il `.magento.app.yaml` file di configurazione.
1. Apri il file per la modifica utilizzando l’editor di testo normale o l’IDE.
1. Imposta la versione richiesta in `hooks:build` sezione. Nell’esempio seguente, la configurazione è impostata per installare NPM v9.5.0, la versione più recente attualmente disponibile (4 febbraio 2019):

   ```yaml
   hooks:
       build: |
           unset NPM_CONFIG_PREFIX
           curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.8/install.sh | bash
           export NVM_DIR="$HOME/.nvm"
           [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
           nvm install 9.5.0
   ```

   >[!NOTE]
   >
   >Se desideri eseguire Node.JS nell’applicazione e non solo nella build, aggiungi i seguenti comandi per modificare l’hook di build:
   > 
   ```
   > echo 'unset NPM_CONFIG_PREFIX' >> .environment
   > echo 'export NO_UPDATE_NOTIFIER=1' >> .environment
   > echo 'export NVM_DIR="$MAGENTO_CLOUD_DIR/.nvm"' >> .environment
   > echo '[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"' >> .environment
   > ```

1. Salva le modifiche nel file.
1. Git invia il file modificato al tuo [ambiente di integrazione](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md).

Le modifiche diventano effettive dopo che Git ha inviato il file YAML aggiornato all’ambiente.

## Documentazione correlata

* [Configurazione dell’applicazione: hook](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/hooks-property.html) nella Guida all’infrastruttura cloud di Adobe Commerce.
