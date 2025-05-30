---
title: Scheda informativa di monitoraggio per  [!DNL Adobe Commerce on cloud pro infrastructure]
description: Questo documento fornisce informazioni sul monitoraggio e le notifiche dell’infrastruttura Adobe Commerce.
exl-id: 01342d8d-2123-4455-b1a5-a08a5805b046
feature: Cloud
source-git-commit: 27fed162416c619a08d757279a3405f1fa72e976
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---


# Scheda informativa di monitoraggio per [!DNL Adobe Commerce on cloud pro infrastructure]

Questo documento fornisce informazioni sul monitoraggio e le notifiche dell’infrastruttura Adobe Commerce.

Il monitoraggio consente ai commercianti, agli integratori di sistemi e ai team interni di Adobe di risolvere eventuali problemi di disponibilità del sito e di spazio su disco insufficiente.

## Risoluzione e risoluzione dei problemi

Le istanze Adobe Commerce in genere contengono codice personalizzato e configurazioni. Adobe non supporta né risolve i problemi relativi al codice personalizzato e alle configurazioni. Adobe aiuta gli esercenti a risolvere eventuali problemi e a identificarli nella nostra knowledge base e fornisce soluzioni consigliate e best practice per la prevenzione e la risoluzione. Incoraggiamo i commercianti e i partner a utilizzare le tabelle seguenti per capire cosa viene monitorato e chi è responsabile della risoluzione.

Quando si attivano le notifiche, il team di supporto Adobe Commerce valuta il problema. Come parte della valutazione, vengono analizzati i registri degli errori e altre risorse. In base al triage, vengono creati ulteriori ticket di supporto [!DNL Zendesk] per gli esercenti o i partner (in caso di aggiornamenti personalizzati) o per i team interni di Adobe per risolvere il problema.

## Adobe Commerce: monitoraggio predefinito

Gli eventi riportati di seguito vengono monitorati e il team di Adobe Commerce adotta le misure necessarie per risolvere e comunicare i problemi identificati.

## Monitoraggio della disponibilità del sito

| Disponibilità del sito | Descrizione |
|------------|------------|
| **Obiettivo di monitoraggio** | Per tenere traccia della disponibilità del sito. |
| **Strumentato su** | Selezione di un singolo [!DNL URL] per un numero elevato di [!DNL SLA]. |
| **Descrizione** | La disponibilità del sito viene determinata in base alle soglie configurate intorno alla metrica. La notifica dell’interruzione del sito viene attivata se il controllo non riesce per 10 minuti e non è in corso alcuna distribuzione attiva. |
| **Destinatario notifica** | Commerciante/Partner e Adobe. |
| **Azione di Adobe** | Responsabile della valutazione e della risoluzione se il problema riguarda l’infrastruttura Adobe Commerce. |
| **Azione dell&#39;esercente** | Responsabile della risoluzione del problema se causato da modifiche o codice personalizzato introdotto da commerciante/partner. Per la risoluzione dei problemi, consultare: [Risoluzione dei problemi di inattività del sito](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.html?lang=it). |

## Monitoraggio dello spazio su disco

| Monitoraggio dello spazio su disco | Descrizione |
|------------|------------|
| **Obiettivo di monitoraggio** | Per tenere traccia dell&#39;utilizzo dello spazio su disco. |
| **Strumentato su** | [!DNL MySQL] partizioni disco e disco multimediale. |
| **Metrica** | Lo spazio libero su disco viene monitorato ogni minuto sull&#39;host. Se rimane solo il 5% o 2 GB di spazio libero, viene visualizzato un avviso. La soglia critica impostata per lo spazio libero rimanente è 2% o 1 GB. |
| **Descrizione** | La notifica viene inviata in base alle soglie configurate per lo spazio libero su disco dell’host. Lo spazio su disco aggiuntivo viene aggiunto automaticamente una sola volta al supporto appropriato ([!DNL MySQL] o supporto) per evitare interruzioni del sito e concedere al commerciante il tempo necessario per liberare spazio su disco e/o per identificare e risolvere eventuali codici o registri che causano un rapido aumento dell&#39;utilizzo del disco. |
| **Destinatario notifica** | Commerciante/Partner e Adobe. |
| **Azione di Adobe** | Aumentare automaticamente il ticket di supporto e aggiungere automaticamente ulteriore spazio su disco al supporto appropriato ([!DNL MySQL] o supporto) per evitare interruzioni del sito. |
| **Azione dell&#39;esercente** | Per ricevere avvisi continui sullo spazio su disco a livello di avviso, fare riferimento a: <ul><li>[[!DNL Managed alerts for Adobe Commerce]: avviso disco](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-disk-warning-alert)</li><li>[[!DNL Managed alerts for Adobe Commerce]: avviso disco critico](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-disk-critical-alert) </li></ul> |
