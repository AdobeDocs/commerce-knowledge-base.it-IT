---
title: Riduzione dei tempi di inattività dell'implementazione su Adobe Commerce su infrastruttura cloud
description: Per ridurre drasticamente i tempi di inattività di manutenzione e fornire una configurazione efficiente dello store tra gli ambienti, Adobe Commerce sull’infrastruttura cloud fornisce la funzione **Gestione della configurazione**. Per l’infrastruttura cloud Adobe Commerce 2.2.x e le implementazioni successive, questa funzione supporta i concetti e le opzioni di distribuzione della pipeline con passaggi ridotti.
exl-id: fde3571c-d95c-4a9b-a024-3b29f9c491ab
feature: Build, Cloud, Configuration, Deploy
source-git-commit: 23d957ceac17f9989d14b215582304199d398545
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---

# Riduzione dei tempi di inattività dell&#39;implementazione su Adobe Commerce su infrastruttura cloud

Per ridurre drasticamente i tempi di inattività di manutenzione e fornire una configurazione efficiente dello store tra gli ambienti, Adobe Commerce sull&#39;infrastruttura cloud fornisce la funzione **Gestione della configurazione**. Per l’infrastruttura cloud Adobe Commerce 2.2.x e le implementazioni successive, questa funzione supporta i concetti e le opzioni di distribuzione della pipeline con passaggi ridotti.

## Panoramica

I problemi che richiedono tempo e denaro per l’implementazione del Web store includono:

* **Applicazione della stessa configurazione in tutti gli ambienti.** In genere, le configurazioni vengono immesse manualmente o tramite complessi aggiornamenti del database. Con Configuration Management, puoi esportare le configurazioni dal database in un singolo file per inviarlo in seguito con il tuo codice dall’ambiente di sviluppo locale a Integration, Staging e Produzione.

* **Inattività del sito durante la distribuzione di contenuto statico.** In genere, il contenuto statico viene distribuito durante la [fase di distribuzione](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process#deploy-phase-deploy-phase). Questa operazione può richiedere fino a 30 minuti o più, il che non è accettabile per gli affari. Gestione configurazione sposta la distribuzione del contenuto statico nella [fase di compilazione](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process#build-phase-build-phase), che non richiede tempi di inattività.

## Versioni della tecnologia

* Adobe Commerce sull&#39;infrastruttura cloud **2.1.4** e versioni successive per Gestione configurazione
* Adobe Commerce sull&#39;infrastruttura cloud **2.2** e versioni successive per la gestione della configurazione e la distribuzione della pipeline

## Che cos’è Configuration Management

Per farla breve, il processo di gestione della configurazione (noto anche come distribuzione delle pipeline) estrae tutte le impostazioni di configurazione dal database Adobe Commerce on Cloud Infrastructure in un unico file PHP. Quindi, aggiungi il file al commit Git e invialo in tutti gli ambienti.

Ciò offre i seguenti vantaggi:

* **Impostazioni coerenti in tutti gli ambienti:** tutte le impostazioni esportate nel file di configurazione vengono bloccate (i campi corrispondenti nell&#39;amministratore di Commerce diventano di sola lettura), il che garantisce configurazioni coerenti quando si invia il file in tutti gli ambienti.
* **Tempi di inattività ridotti:** la distribuzione dei file statici passa dalla [fase di distribuzione](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process#deploy-phase-deploy-phase) (che richiede che il sito sia in modalità di manutenzione) alla [fase di compilazione](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process#build-phase-build-phase) (quando il sito non è in modalità di manutenzione e non verrà disattivato in caso di errori o problemi).
* **Dati sensibili protetti:** con Adobe Commerce sull&#39;infrastruttura cloud 2.2 e versioni successive, il processo esporta anche i dati sensibili (ad esempio le credenziali del gateway di pagamento) nel file `env.php`. Questo file deve essere salvato solo nell’ambiente in cui viene creato e non inviato con i rami Git.

Si consiglia vivamente di applicare l’approccio di gestione della configurazione nell’implementazione.

## Gestione della configurazione nella documentazione per gli sviluppatori

* [Gestione della configurazione per **2.1.X**](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) e [example](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) nella *Guida all&#39;infrastruttura cloud di Adobe Commerce*
* [Gestione della configurazione per **2.2.X**](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) e [example](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) nella *Guida all&#39;infrastruttura cloud di Adobe Commerce*
* [Aggiornamento da 2.0.X o 2.1.X](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version.html#upgrade-from-older-versions) sezione dell&#39;argomento *Aggiornamento di Adobe Commerce sull&#39;infrastruttura cloud*
* [Distribuzione della pipeline](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/overview.html) nella *Guida di configurazione di Adobe Commerce sull&#39;infrastruttura cloud* - Per Adobe Commerce sull&#39;infrastruttura cloud, non è necessario seguire le istruzioni riportate in questa guida. Il contenuto è esclusivamente a scopo di riferimento. Adobe Commerce fornisce già il server di build, gli ambienti di integrazione e altro ancora sull’infrastruttura cloud.
