---
title: Abilitare la cache per evitare il deterioramento delle prestazioni
description: Questo articolo spiega come risolvere un problema di sito lento causato dalla disabilitazione di alcuni tipi di cache di Adobe Commerce.
exl-id: e4e5a753-efa3-4552-aaf6-28e44efcfa5b
feature: Cache, Observability
role: Developer
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# Abilitare la cache per evitare il deterioramento delle prestazioni

Questo articolo spiega come risolvere un problema di sito lento causato dalla disabilitazione di alcuni tipi di cache di Adobe Commerce.

## Prodotti e versioni interessati

* Adobe Commerce sull’infrastruttura cloud 2.2.x, 2.3.x
* Adobe Commerce on-premise 2.2.x, 2.3.x

## Problema

Notate un peggioramento delle prestazioni. Ad esempio, il caricamento della pagina Checkout è lento o il valore Apdex diminuisce in New Relic.

## Causa

Uno dei motivi del peggioramento delle prestazioni potrebbe essere la disabilitazione di alcuni tipi di cache di Adobe Commerce.

## Soluzione

1. Innanzitutto, controlla lo stato della cache di Adobe Commerce per verificare se è questo il problema. Per questo, [SSH nel tuo ambiente](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/secure-connections#ssh) ed esegui il seguente comando:

   ```bash
   php bin/magento cache:status
   ```

   Questo mostrerebbe lo stato di ciascun tipo di cache (&quot;0&quot; per disabilitato, &quot;1&quot; per abilitato). Oppure è possibile ottenere queste informazioni nel file `app/etc/env.php`.

1. Esaminare i tipi di cache disabilitati. Tutti i tipi di cache di Adobe Commerce devono essere abilitati, a meno che tu non abbia ricevuto indicazioni alternative da Adobe. Le estensioni di terze parti non devono richiedere la disabilitazione della cache di Adobe Commerce.
1. Se l&#39;indagine conferma che alcuni tipi di cache sono disabilitati per errore, abilitarli eseguendo il comando seguente per ogni tipo di cache: `php bin/magento cache:enable <your_disabled_cache_type>`

In caso di dubbi e/o domande sulla possibilità o meno di disabilitare un determinato tipo di cache di Adobe Commerce, [contatta il supporto Adobe Commerce](https://experienceleague.adobe.com/it/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide) per richiedere consigli.

## Lettura correlata

Documentazione della cache di Adobe Commerce nella documentazione per gli sviluppatori:

* [Panoramica della cache di Adobe Commerce](https://developer.adobe.com/commerce/frontend-core/guide/caching/)
* [Gestione della cache](https://experienceleague.adobe.com/it/docs/commerce-operations/configuration-guide/cli/manage-cache)

Altri possibili motivi per problemi di prestazioni e relative soluzioni:

* [Disattiva l&#39;output del banner Adobe Commerce per migliorare le prestazioni del sito](https://experienceleague.adobe.com/it/docs/experience-cloud-kcs/kbarticles/ka-26909)
* [Le tabelle MySQL sono troppo grandi](https://experienceleague.adobe.com/it/docs/experience-cloud-kcs/kbarticles/ka-26945)
* [Prestazioni lente, esecuzione lenta e cronica prolungata](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md)