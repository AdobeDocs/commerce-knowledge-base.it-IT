---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.0.6'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in  [!DNL Quality Patches Tool] (QPT) v1.0.6.
exl-id: 38e9454b-e278-4b14-a861-2af0623db92e
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---

# Panoramica di [!DNL Quality Patches Tool] (QPT) v1.0.6

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.0.6.

QPT v1.0.6 include le seguenti patch:

1. **MDVA-28202**: è stato risolto il problema che impediva a Layered Navigation di filtrare correttamente i prodotti configurabili quando viene utilizzato MSI.
1. **MDVA-28300**: è stato risolto il problema che impediva alla richiesta GQL di riflettere le modifiche di prezzo dalle regole di prezzo del catalogo.
1. **MDVA-28993**: implementa *Minimum deve corrispondere* funzionalità e ricerca parziale per il motore [!DNL Elasticsearch]. Risolve i problemi relativi ai trattini nelle query di ricerca.
1. **MDVA-29446**: è stato risolto il problema che causava la visualizzazione dello zero del prezzo del metodo di spedizione non applicabile durante l&#39;estrazione.
1. **MDVA-29787**: è stato risolto il problema che causava il mancato funzionamento della regola di destinazione per i prodotti correlati quando *è una delle* condizioni utilizzate per definire i prodotti da visualizzare.
1. **MDVA-30102**: è stato risolto il problema che provoca la rapida espansione della cache di [!DNL Redis], poiché le cache di layout non dispongono di TTL.
1. **MDVA-30357**: è stato risolto il problema relativo alla creazione di URL di immagine errati durante la generazione di una sitemap da cron.
1. **MDVA-30565**: è stato risolto il problema che causava la visualizzazione dell&#39;errore *Nessuna entità con cartid = 0* per il cliente ospite all&#39;estrazione in vetrina se il carrello acquisti persistente era abilitato.
1. **MDVA-30599**: è stato corretto il problema a causa del quale le virgolette dei guest create utilizzando l&#39;API vengono contrassegnate in modo errato come virgolette per i clienti connessi.
1. **MDVA-30977**: è stato corretto il problema di mancanza di prodotti casuali nelle categorie dopo la reindicizzazione.
1. **MDVA-31006**: è stato risolto il problema relativo alla visualizzazione di ordini duplicati dopo l&#39;invio di un ordine tramite il pagamento [!DNL Paypal Express].

Utilizza il menu a sinistra per passare a una pagina patch specifica.
