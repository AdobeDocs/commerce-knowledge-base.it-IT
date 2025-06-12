---
title: Disattiva l'output del banner Adobe Commerce per migliorare le prestazioni del sito
description: Questo articolo fornisce una correzione per le basse prestazioni del sito. Le basse prestazioni del sito possono essere causate dal modulo "Magento_Banner" che viene attivato ma non utilizzato. La disattivazione dell’output del modulo può migliorare le prestazioni del sito. Consulta l’articolo per i passaggi di risoluzione.
exl-id: 90a8bd21-1f2c-4cfe-8213-17f877e20de8
feature: Configuration
role: Developer
source-git-commit: 76ef59dc37504f50d55734a90c9ce5b30bb83175
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# Disattiva l&#39;output del banner Adobe Commerce per migliorare le prestazioni del sito

Questo articolo fornisce una correzione per le basse prestazioni del sito. Il modulo `Magento_Banner` è abilitato ma non utilizzato a causa di prestazioni del sito insufficienti. La disattivazione dell’output del modulo può migliorare le prestazioni del sito. Consulta l’articolo per i passaggi di risoluzione.

>[!NOTE]
>
>Se utilizzi la funzionalità banner di Adobe Commerce, consulta l&#39;articolo [Le richieste AJAX a throughput elevato causano prestazioni scadenti](/help/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.md) nella knowledge base di supporto per raccomandazioni su come evitare problemi di prestazioni causati da richieste Ajax eccessive.

## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud v.2.x.x
* Adobe Commerce on-premise v.2.2.x e 2.3.x

## Problema

Il modulo `Magento_Banner` è abilitato, ma non utilizzato.

Per verificare se questo è il caso:

Per Adobe Commerce su infrastruttura cloud 2.2.x:

1. Accedi all’amministratore di Commerce.
1. Passa a **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Banners]**.
1. Se la griglia visualizzata in questa pagina è vuota, non sono presenti banner.

Se non trovi l&#39;opzione **[!UICONTROL Banners]** in **[!UICONTROL Content]** > **[!UICONTROL Elements]**, significa che hai già applicato i consigli di questo articolo.

Per Adobe Commerce su infrastruttura cloud 2.3.x e versioni successive (la funzionalità era [rinominata nella versione 2.3.x](https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/ReleaseNotes2.3.0Commerce.html#banner-now-dynamic-block)):

1. Accedi all’amministratore di Commerce.
1. Passa a **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Dynamic Blocks]**.
1. Se la griglia visualizzata in questa pagina è vuota, non sono presenti blocchi dinamici (banner).

Se non trovi l&#39;opzione **[!UICONTROL Dynamic Blocks]** in **[!UICONTROL Content]** > **[!UICONTROL Elements]**, significa che hai già applicato il consiglio di questo articolo. Per visualizzare nuovamente l&#39;opzione dei banner, invertire il processo.

## Causa

Quando il modulo `Magento_Banner` è abilitato, Adobe Commerce invia richieste Ajax dalla vetrina al server per ottenere le informazioni del banner. Queste richieste Ajax hanno un impatto sulle prestazioni, soprattutto in condizioni di carico elevato (volume elevato e traffico elevato). Se questa funzionalità non viene utilizzata, si consiglia di disabilitare l’output del modulo. Si sconsiglia di disattivare il modulo a causa di problemi di dipendenza.

## Soluzione

>[!WARNING]
>
>È consigliabile testare le modifiche nell&#39;ambiente di [staging/integrazione](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) prima di applicarle all&#39;ambiente di produzione. Consigliamo inoltre di avere un backup recente prima di qualsiasi manipolazione.

1. Disattivare l&#39;output del modulo `Magento_Banner`, come descritto in [Disattivare l&#39;output del modulo](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/files/disable-module-output) nella documentazione per gli sviluppatori. Il nome del modulo da utilizzare è `Magento_Banner`.
1. Distribuisci il codice. Per Adobe Commerce su infrastruttura cloud, esegui la distribuzione come descritto nell&#39;articolo [Distribuisci il tuo archivio](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/staging-production) nella documentazione per gli sviluppatori.
1. Dopo aver disabilitato l’output del modulo, il menu non viene più visualizzato nell’amministratore.
1. Non vedrai più il banner o l&#39;opzione dinamica in **[!UICONTROL Content]** > **[!UICONTROL Elements]**. Per visualizzare nuovamente le opzioni, [abilita l&#39;output del modulo](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/files/disable-module-output?lang=en#disable-module-output-in-a-simple-deployment).

