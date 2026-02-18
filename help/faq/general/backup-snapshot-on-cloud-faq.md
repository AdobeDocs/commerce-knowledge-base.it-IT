---
title: 'Backup (snapshot) su Cloud: domande frequenti'
description: Questo articolo illustra le nozioni di base per il backup degli ambienti con istantanee su Adobe Commerce su infrastrutture cloud.
exl-id: 0077db74-3e7e-4c98-b215-7f6c089f49e8
feature: Cloud, Iaas
source-git-commit: 9e218e3fadbf9941c94d309fcfb6f258d2f4faf2
workflow-type: tm+mt
source-wordcount: '709'
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
* Gli snapshot automatici vengono creati **indipendentemente dallo stato attivo** del sito (gli snapshot vengono creati anche per i siti non ancora avviati). I backup automatici non sono accessibili pubblicamente perché sono archiviati in un sistema separato.
Puoi [inviare un ticket di supporto Adobe Commerce](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide) per richiedere un backup speciale o per eseguire il ripristino da un backup specifico, specificando la data, l&#39;ora e il fuso orario nel ticket. Dopo che il team dell&#39;infrastruttura ha fornito lo snapshot, per determinare il timestamp in cui è stato originariamente creato, eseguire il comando seguente dal percorso in cui è stato inserito lo snapshot:

  `cat /mnt/recovery/vol-<volume_id>/snap.time`

  Esempio di output:

  <strong>2025-01-13 08:42:17,123000+00:00</strong>


* Il supporto non genera snapshot manuali su richiesta. Inoltre, il supporto non esegue automaticamente il rollback o il ripristino del database, poiché recupera lo snapshot, ma è necessario ripristinare il database manualmente.
* Gli snapshot automatici vengono creati **indipendentemente dallo stato attivo** del sito (gli snapshot vengono creati anche per i siti non ancora avviati). I backup automatici sono archiviati in un sistema separato e non sono accessibili al pubblico.
Puoi [inviare un ticket di supporto Adobe Commerce](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide) per richiedere un backup speciale o per eseguire il ripristino da un backup specifico, specificando la data, l&#39;ora e il fuso orario nel ticket. Il supporto non genera snapshot manuali su richiesta.
Inoltre, il supporto non esegue automaticamente il rollback o il ripristino del database, poiché recupera lo snapshot, ma è necessario ripristinare il database manualmente.
* I backup vengono creati utilizzando **snapshot crittografati di Amazon Web Services Elastic Block Store (AWS EBS)**.
* Le istantanee dell’ambiente includono l’intero sistema (file system e database).
* Il tempo di conservazione per gli snapshot automatici **è diverso** e segue [la pianificazione](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/architecture/pro-architecture#backup-and-disaster-recovery).

>[!NOTE]
>
>La console cloud mostra sempre [!UICONTROL No backup] negli ambienti di staging e produzione. È possibile eseguire backup solo dall’ambiente di integrazione. Selezionare **[!UICONTROL Backup]** nel menu a discesa con i puntini di sospensione.
>
>![cloud_console_backup.png](assets/cloud_console_backup.png)

### Ambiente di integrazione (sviluppo)

* [Il backup dell&#39;ambiente di integrazione](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27242) non viene eseguito automaticamente **&#x200B;**, ma è possibile creare istantanee **manualmente**.
* Puoi creare istantanee manuali per gli ambienti di integrazione su store non live.
* Potresti avere **più snapshot** che sono stati attivati manualmente.
* Uno snapshot attivato manualmente è archiviato per **7 giorni**.

**Articoli correlati nella documentazione per gli sviluppatori:**

* [Backup e disaster recovery](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/architecture/pro-architecture#backup-and-disaster-recovery)
* [Crea uno snapshot](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/storage/snapshots)

## Istantanea dell’ambiente, piano iniziale

* Il backup di tutti i tipi di ambienti (integrazione, gestione temporanea, produzione) **non viene eseguito automaticamente**, ma è possibile creare istantanee manualmente.
* È possibile creare istantanee manuali **indipendentemente dallo stato attivo** del sito (create anche per siti non ancora avviati).
* Uno snapshot attivato manualmente è archiviato per **7 giorni**.

## Ripristinare uno snapshot dell’ambiente

Per ripristinare uno snapshot esistente (nell&#39;ambiente supportato: integrazione, gestione temporanea, produzione su piano Starter o integrazione su piano Pro), seguire i passaggi descritti in [Gestione backup: ripristino di un backup manuale](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#restore-a-manual-backup) nella Guida all&#39;infrastruttura Commerce su Cloud.

## Backup database (DB)

Il backup del database fa parte di un&#39;istantanea cloud:

Uno snapshot è un backup completo di un ambiente che include tutti i dati persistenti di tutti i servizi in esecuzione (ad esempio, **il database MySQL**, Redis e così via) e tutti i file archiviati nei volumi montati.

>[!NOTE]
>
>I volumi montati includono/fanno riferimento solo ai [mount scrivibili](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/properties/properties#mounts) e non includeranno tutta la directory `/app`. Come per gli altri file, questi vengono creati/generati da [il processo di compilazione e distribuzione](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/architecture/pro-develop-deploy-workflow#deployment-workflow) e sarà necessario estrarre i file rimanenti dall&#39;archivio Git.

[Snapshot e gestione dei backup](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/storage/snapshots) nella documentazione per gli sviluppatori.

Invia una [richiesta di supporto](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide) per uno snapshot del database da Pro Production e Staging solo se il database è necessario da un momento specifico. Se hai bisogno solo di un backup corrente del tuo database (in qualsiasi ambiente), consulta l&#39;articolo della knowledge base: [Genera immagini di database su Cloud](/help/how-to/general/create-database-dump-on-cloud.md).
