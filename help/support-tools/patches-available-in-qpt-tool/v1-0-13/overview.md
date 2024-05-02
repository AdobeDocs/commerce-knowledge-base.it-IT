---
title: '"Panoramica: [!DNL Quality Patches Tool] (QPT) v1.0.13'''
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.0.13.
exl-id: c25d2926-2137-4a55-abb2-8c0cbff184c9
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) Panoramica della versione 1.0.13

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.0.13.

QPT v1.0.13 include le seguenti patch:

1. **MCP-87**: è stato migliorato il tempo di indicizzazione per gli indicizzatori di prodotti e azioni per categorie per i profili di grandi dimensioni.
1. **MDVA-13203**: risolve il problema relativo alla presenza di *Tabella search_tmp_ della violazione del vincolo di integrità* dopo una reindicizzazione completa viene visualizzato un errore.
1. **MDVA-19391**: risolve il problema in cui `analytics_collect_data` sta generando un errore a causa di record di descrizione NULL nel `catalog_category_entity_text` tabella.
1. **MDVA-20376**: risolve il problema con *Nessuna entità di questo tipo con customerId = 1* errore in `exception.log` per i clienti connessi dopo il posizionamento dell’ordine.
1. **MDVA-22150**: risolve il problema per cui i clienti con un prodotto configurabile nel carrello e un coupon applicato non possono accedere se tale prodotto configurabile è disabilitato in Amministrazione.
1. **MDVA-23426**: risolve il problema per cui le e-mail di notifica inviate da Adobe Commerce contengono un corpo vuoto con il contenuto aggiunto come allegato.
1. **MDVA-23764**: corregge il bug in `JsFooterPlugin.php` che influisce sulla visualizzazione dei blocchi dinamici.
1. **MDVA-30858**: risolve il problema con [!DNL PayPal] I rapporti sulle liquidazioni non sono disponibili in **[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL PayPal]** Liquidazione come previsto.
1. **MDVA-32545**: corregge il problema che impediva l’invio automatico delle fatture durante la creazione degli ordini dall’Amministratore.
1. **MDVA-32714**: è stato risolto il problema che impediva il corretto funzionamento del prezzo di gruppo del cliente nella query del prodotto GraphQL.
1. **MDVA-33106**: risolve il problema relativo alla cancellazione delle modifiche al prodotto ripianificate dopo il cron `run` viene eseguito.

Utilizza il menu a sinistra per passare a una pagina patch specifica.
