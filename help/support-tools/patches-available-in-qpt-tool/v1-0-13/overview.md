---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.0.13'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in  [!DNL Quality Patches Tool] (QPT) v1.0.13.
exl-id: c25d2926-2137-4a55-abb2-8c0cbff184c9
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# Panoramica di [!DNL Quality Patches Tool] (QPT) v1.0.13

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.0.13.

QPT v1.0.13 include le seguenti patch:

1. **MCP-87**: è stato migliorato il tempo di indicizzazione per gli indicizzatori di prodotti e azioni per i profili di grandi dimensioni.
1. **MDVA-13203**: è stato risolto il problema che causava la visualizzazione dell&#39;errore *Violazione del vincolo di integrità search_tmp_ table* dopo una reindicizzazione completa.
1. **MDVA-19391**: è stato corretto il problema a causa del quale `analytics_collect_data` genera un errore a causa di record di descrizione NULL nella tabella `catalog_category_entity_text`.
1. **MDVA-20376**: è stato risolto il problema con *Nessuna entità di questo tipo con customerId = 1* errore in `exception.log` per i clienti connessi dopo l&#39;inserimento dell&#39;ordine.
1. **MDVA-22150**: è stato risolto il problema che impediva ai clienti con un prodotto configurabile nel carrello e un coupon applicato di accedere se tale prodotto configurabile era disabilitato in Amministrazione.
1. **MDVA-23426**: è stato corretto il problema per cui le e-mail di notifica inviate da Adobe Commerce contenevano un corpo vuoto con contenuto aggiunto come allegato.
1. **MDVA-23764**: è stato corretto il bug in `JsFooterPlugin.php` che influisce sulla visualizzazione dei blocchi dinamici.
1. **MDVA-30858**: è stato risolto il problema che impediva la disponibilità dei report di liquidazione [!DNL PayPal] in **[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL PayPal]** come previsto.
1. **MDVA-32545**: è stato risolto il problema che impediva l&#39;invio automatico delle fatture durante la creazione di ordini dall&#39;amministratore.
1. **MDVA-32714**: è stato risolto il problema che impediva il funzionamento del prezzo del gruppo di clienti nella query del prodotto GraphQL.
1. **MDVA-33106**: è stato risolto il problema che causava la cancellazione delle modifiche del prodotto ripianificate dopo l&#39;esecuzione del comando cron `run`.

Utilizza il menu a sinistra per passare a una pagina patch specifica.
