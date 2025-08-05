---
title: Configurare NPM per l'utilizzo di PWA Studio
description: '[Progressive Web Apps (PWA) Studio](https://magento.github.io/pwa-studio/) è un nuovo progetto disponibile per Adobe Commerce su infrastruttura cloud 2.3.x o versione successiva. Per poter utilizzare e installare PWA Studio, è necessario impostare la versione di Gestione pacchetti NPM su 5.x o successiva per ottenere il supporto per Node.js 8.x. Questa operazione viene eseguita nella sezione "hooks:build" del file di configurazione &grave;.magento.app.yaml&grave;.'
exl-id: 3854fc94-e8ad-45d8-bf3e-73462364220d
source-git-commit: 139c2836ba36686357c7a5458a36550c7b1273c1
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# Configurare NPM per l&#39;utilizzo di PWA Studio

[Progressive Web Apps (PWA) Studio](https://magento.github.io/pwa-studio/) è un nuovo progetto disponibile per Adobe Commerce su infrastruttura cloud 2.3.x o versione successiva. Per poter utilizzare e installare PWA Studio, è necessario impostare la versione di Gestione pacchetti NPM su 5.x o successiva per ottenere il supporto per Node.js 8.x. Operazione eseguita nella sezione `hooks:build` del file di configurazione `.magento.app.yaml`.

## Ambiente e tecnologie

* Adobe Commerce sull’infrastruttura cloud 2.3.X
* PWA per Adobe Commerce

## Imposta versione NPM: passaggi

Per impostare la versione NPM necessaria, specificarla nel file di configurazione `.magento.app.yaml`. Segui questi passaggi:

1. Nell&#39;ambiente di sviluppo locale individuare il file di configurazione `.magento.app.yaml`.
1. Apri il file per la modifica utilizzando l’editor di testo normale o l’IDE.
1. Impostare la versione richiesta nella sezione `hooks:build`. Nell’esempio seguente, la configurazione è impostata per installare NPM v9.5.0, la versione più recente attualmente disponibile (4 febbraio 2019):

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
   > ```
   > echo 'unset NPM_CONFIG_PREFIX' >> .environment
   > echo 'export NO_UPDATE_NOTIFIER=1' >> .environment
   > echo 'export NVM_DIR="$MAGENTO_CLOUD_DIR/.nvm"' >> .environment
   > echo '[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"' >> .environment
   > ```

1. Salva le modifiche nel file.
1. Git invia il file modificato all&#39;[ambiente di integrazione](https://experienceleague.adobe.com/it/docs/experience-cloud-kcs/kbarticles/ka-27242).

Le modifiche diventano effettive dopo che Git ha inviato il file YAML aggiornato all’ambiente.

## Documentazione correlata

* [Configurazione dell&#39;applicazione: hook](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/hooks-property.html?lang=it) nella Guida all&#39;infrastruttura di Adobe Commerce su Cloud.
