---
title: Disattiva l'output del banner Adobe Commerce per migliorare le prestazioni del sito
description: Questo articolo fornisce una correzione per le basse prestazioni del sito. Le basse prestazioni del sito possono essere causate dall’attivazione ma non utilizzo del modulo "Magento_Banner". La disattivazione dell’output del modulo può migliorare le prestazioni del sito. Consulta l’articolo per i passaggi di risoluzione.
exl-id: 90a8bd21-1f2c-4cfe-8213-17f877e20de8
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Disattiva l&#39;output del banner Adobe Commerce per migliorare le prestazioni del sito

Questo articolo fornisce una correzione per le basse prestazioni del sito. Le prestazioni ridotte del sito possono essere causate da `Magento_Banner` modulo abilitato ma non utilizzato. La disattivazione dell’output del modulo può migliorare le prestazioni del sito. Consulta l’articolo per i passaggi di risoluzione.

>[!NOTE]
>
>Se utilizzi la funzionalità banner di Adobe Commerce, consulta [Le richieste AJAX a throughput elevato causano prestazioni insoddisfacenti](/help/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.md) articolo nella knowledge base di supporto per consigli su come evitare problemi di prestazioni causati da richieste Ajax eccessive.

## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud v.2.x.x
* Adobe Commerce on-premise v.2.2.x e 2.3.x

## Problema

Il `Magento_Banner` il modulo è attivato, ma non utilizzato.

Per verificare se questo è il caso:

Per Adobe Commerce su infrastruttura cloud 2.2.x:

1. Accedi all’amministratore di Commerce.
1. Accedi a **Contenuto** > *Elementi* > **Banner**.
1. Se la griglia visualizzata in questa pagina è vuota, non sono presenti banner.

Se non vede il **Banner** opzione in **Contenuto** > *Elementi* Quindi non è così e le raccomandazioni di questo articolo non possono essere applicate.

Per Adobe Commerce su infrastruttura cloud 2.3.x (la funzionalità era [rinominato nella versione 2.3.x](https://devdocs.magento.com/guides/v2.3/release-notes/ReleaseNotes2.3.0Commerce.html#banner-now-dynamic-block)):

1. Accedi all’amministratore di Commerce.
1. Accedi a **Contenuto** > *Elementi >*  **Blocchi dinamici**.
1. Se la griglia visualizzata in questa pagina è vuota, non sono presenti blocchi dinamici (banner).

Se non vede il **Blocchi dinamici** opzione in **Contenuto** > *Elementi* Quindi non è così e le raccomandazioni di questo articolo non possono essere applicate.

## Causa

Quando `Magento_Banner` Se il modulo è abilitato, Adobe Commerce invia richieste Ajax dalla vetrina al server per ottenere le informazioni del banner. Queste richieste Ajax hanno un impatto sulle prestazioni, soprattutto in condizioni di carico elevato (volume elevato e traffico elevato). Se questa funzionalità non viene utilizzata, si consiglia di disabilitare l’output del modulo. Si sconsiglia di disattivare il modulo a causa di problemi di dipendenza.

## Soluzione

>[!WARNING]
>
>È consigliabile testare le modifiche su [Ambiente di staging/integrazione](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) in primo luogo, prima di applicarlo alla Produzione. Consigliamo inoltre di avere un backup recente prima di qualsiasi manipolazione.

1. Disattiva il `Magento_Banner` output del modulo, come descritto [Disattiva output modulo](https://devdocs.magento.com/guides/v2.3/config-guide/config/disable-module-output.html) nella documentazione per gli sviluppatori. Il nome del modulo da utilizzare è `Magento_Banner`.
1. Distribuisci il codice. Per l’infrastruttura cloud di Adobe Commerce, distribuisci come descritto nella sezione [Distribuire lo store](https://devdocs.magento.com/guides/v2.3/cloud/live/stage-prod-live.html) articolo nella documentazione per gli sviluppatori.
