---
title: Scheda tecnica di monitoraggio per [!DNL Adobe Commerce on cloud pro infrastructure]
description: Questo documento fornisce informazioni sul monitoraggio e le notifiche dell’infrastruttura Adobe Commerce.
exl-id: 01342d8d-2123-4455-b1a5-a08a5805b046
feature: Cloud
source-git-commit: 4926bcff19b8c4c7e2a9a9dfb0cb1fc72a9821ba
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---


# Scheda tecnica di monitoraggio per [!DNL Adobe Commerce on cloud pro infrastructure]

Questo documento fornisce informazioni sul monitoraggio e le notifiche dell’infrastruttura Adobe Commerce.

Il monitoraggio consente ai commercianti, agli integratori di sistemi e ai team interni di Adobe di risolvere eventuali problemi di disponibilità del sito e di spazio su disco insufficiente.

## Risoluzione e risoluzione dei problemi

Le istanze Adobe Commerce in genere contengono codice personalizzato e configurazioni. L’Adobe non supporta né risolve i problemi relativi al codice personalizzato e alle configurazioni. Adobe aiuta i commercianti a risolvere i problemi e a identificarli nella nostra knowledge base e fornisce soluzioni consigliate e best practice per la prevenzione e la risoluzione. Incoraggiamo i commercianti e i partner a utilizzare le tabelle seguenti per capire cosa viene monitorato e chi è responsabile della risoluzione.

Quando si attivano le notifiche, il team di supporto Adobe Commerce valuta il problema. Come parte della valutazione, vengono analizzati i registri degli errori e altre risorse. In base al triage, ulteriori [!DNL Zendesk] i ticket di supporto vengono creati per gli esercenti o i partner (in caso di aggiornamenti personalizzati) o per i team interni di Adobe per risolvere il problema.

## Adobe Commerce: monitoraggio predefinito

Gli eventi riportati di seguito vengono monitorati e il team di Adobe Commerce adotta le misure necessarie per risolvere e comunicare i problemi identificati.

## Monitoraggio della disponibilità del sito

| Disponibilità del sito | Descrizione |
|------------|------------|
| **Obiettivo di monitoraggio** | Per tenere traccia della disponibilità del sito. |
| **Strumentato su** | Singolo [!DNL URL] selezionato per alta [!DNL SLA]. |
| **Descrizione** | La disponibilità del sito viene determinata in base alle soglie configurate intorno alla metrica. La notifica dell’interruzione del sito viene attivata se il controllo non riesce per 10 minuti e non è in corso alcuna distribuzione attiva. |
| **Destinatario notifica** | Commerciante/partner e Adobe. |
| **Azione per Adobe** | Responsabile della valutazione e della risoluzione se il problema riguarda l’infrastruttura Adobe Commerce. |
| **Azione dell&#39;esercente** | Responsabile della risoluzione del problema se causato da modifiche o codice personalizzato introdotto da commerciante/partner. Per la risoluzione dei problemi, fare riferimento a: [Risoluzione dei problemi di inattività del sito](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.html). |

## Monitoraggio dello spazio su disco

| Monitoraggio dello spazio su disco | Descrizione |
|------------|------------|
| **Obiettivo di monitoraggio** | Per tenere traccia dell&#39;utilizzo dello spazio su disco. |
| **Strumentato su** | [!DNL MySQL] partizioni di dischi e supporti. |
| **Metrica** | Lo spazio libero su disco viene monitorato ogni minuto sull&#39;host. Se rimane solo il 5% o 2 GB di spazio libero, viene visualizzato un avviso. La soglia critica impostata per lo spazio libero rimanente è 2% o 1 GB. |
| **Descrizione** | La notifica viene inviata in base alle soglie configurate per lo spazio libero su disco dell’host. Lo spazio su disco aggiuntivo viene aggiunto automaticamente una sola volta al supporto appropriato ([!DNL MySQL] o supporti) per evitare interruzioni del sito e dare al commerciante il tempo di liberare spazio su disco e/o identificare e risolvere eventuali codici o registri che causano un rapido aumento dell&#39;utilizzo del disco. |
| **Destinatario notifica** | Commerciante/partner e Adobe. |
| **Azione per Adobe** | Aumentare automaticamente il ticket di supporto e aggiungere automaticamente spazio su disco al relativo montaggio ([!DNL MySQL] o dei supporti) per evitare l&#39;interruzione del sito. |
| **Azione dell&#39;esercente** | Per ricevere avvisi continui sullo spazio su disco a livello di avviso, fare riferimento a: <ul><li>[[!DNL Managed alerts for Adobe Commerce]: avviso del disco](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce-disk-warning-alert.html)</li><li>[[!DNL Managed alerts for Adobe Commerce]: avviso critico del disco](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce-disk-critical-alert.html) </li></ul> |
