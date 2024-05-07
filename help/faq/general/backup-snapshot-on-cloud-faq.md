---
title: "Backup (snapshot) su cloud: domande frequenti"
description: Questo articolo illustra le nozioni di base per il backup degli ambienti con istantanee su Adobe Commerce su infrastrutture cloud.
exl-id: 0077db74-3e7e-4c98-b215-7f6c089f49e8
feature: Cloud, Iaas
source-git-commit: 0958a8923e27c1341f4b536812b26205685b2b81
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 0%

---

# Backup (snapshot) su Cloud: domande frequenti

Questo articolo descrive il backup degli ambienti con istantanee sull’infrastruttura cloud di Adobe Commerce.

## Prodotti e versioni interessati

* Adobe Commerce sull’infrastruttura cloud 2.4.x
* Piani dell&#39;architettura: Starter, Pro Legacy, Pro

## Snapshot dell&#39;ambiente, piano Pro

### Ambienti di staging e produzione

* Le istantanee manuali non sono disponibili per gli ambienti di staging e produzione su piano Pro.
* Vengono creati snapshot automatici **indipendentemente dallo stato live** del sito (sono state create anche istantanee per siti non ancora avviati). I backup automatici non sono accessibili pubblicamente perché sono archiviati in un sistema separato. È possibile [invia un ticket di supporto Adobe Commerce](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) per richiedere un backup speciale o per ripristinare da un backup specifico fornendo la data, l’ora e il fuso orario nel ticket. Inoltre, il supporto non esegue automaticamente il rollback o il ripristino del database, poiché recupera lo snapshot, ma è necessario ripristinare il database manualmente.
* I backup vengono creati utilizzando **snapshot crittografate di Amazon Web Services Elastic Block Store (AWS EBS)**.
* Le istantanee dell’ambiente includono l’intero sistema (file system e database).
* Tempo di conservazione per gli snapshot automatici **è diverso** e segue [la pianificazione](/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html?lang=en#backup-and-disaster-recovery).

>[!NOTE]
>La console Cloud viene sempre visualizzata [!UICONTROL No backup] negli ambienti di staging e produzione. È possibile eseguire backup solo dall’ambiente di integrazione. Seleziona **[!UICONTROL Backup]** nel menu a discesa con i puntini di sospensione.
>![cloud_console_backup.png](assets/cloud_console_backup.png)





### Ambiente di integrazione (sviluppo)

* Il tuo [Ambiente di integrazione](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) è **backup non eseguito automaticamente**, ma è possibile creare snapshot **manualmente**.
* Puoi creare istantanee manuali per gli ambienti di integrazione su store non live.
* È possibile che **più snapshot** che sono stati attivati manualmente.
* Viene memorizzata una copia istantanea attivata manualmente per **7 giorni**.

**Articoli correlati nella documentazione per gli sviluppatori:**

* [Backup e disaster recovery](/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html#backup-and-disaster-recovery)
* [Creare un’istantanea](/docs/commerce-cloud-service/user-guide/develop/storage/snapshots.html)

## Istantanea dell’ambiente, piano iniziale

* Tutti i tipi di ambienti (integrazione, staging, produzione) **non vengono sottoposti automaticamente a backup**, ma è possibile creare istantanee manualmente.
* È possibile creare snapshot manuali **indipendentemente dallo stato live** del sito (sono state create anche istantanee per siti non ancora avviati).
* Viene memorizzata una copia istantanea attivata manualmente per **7 giorni**.

## Ripristinare uno snapshot dell’ambiente

Per ripristinare uno snapshot esistente (nell&#39;ambiente supportato: integrazione, staging, produzione su piano Starter o integrazione su piano Pro), seguire i passaggi descritti in [Gestione dei backup: ripristino di un backup manuale](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#restore-a-manual-backup) nella Guida all’infrastruttura Commerce on Cloud.

## Backup database (DB)

Il backup del database fa parte di un&#39;istantanea cloud:

>>
Un&#39;istantanea è un backup completo di un ambiente che include tutti i dati persistenti di tutti i servizi in esecuzione (ad esempio, **database MySQL**, Redis e così via) e tutti i file archiviati nei volumi montati.

>[!NOTE]
>
>I volumi montati includono/fanno riferimento solo al [supporti scrivibili](/docs/commerce-cloud-service/user-guide/configure/app/properties/properties.html?lang=en#mounts) e non includerà tutta la directory /app. Come per gli altri file, vengono creati/generati da [il processo di compilazione e distribuzione](/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html?lang=en#deployment-workflow)e sarà inoltre necessario estrarre i file rimanenti dall’archivio Git.

[Snapshot e gestione dei backup](/docs/commerce-cloud-service/user-guide/develop/storage/snapshots.html) nella documentazione per gli sviluppatori.

Invia solo un [richiesta di supporto](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket) per un&#39;istantanea del database da Pro Production e Staging se è necessario il database da un momento specifico. Se è necessario un backup corrente solo del database (in qualsiasi ambiente), vedere l&#39;articolo della knowledge base: [Generare le immagini del database nel cloud](/help/how-to/general/create-database-dump-on-cloud.md).
