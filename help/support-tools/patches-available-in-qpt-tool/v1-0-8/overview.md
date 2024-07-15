---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.0.8'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in  [!DNL Quality Patches Tool] (QPT) v1.0.8.
exl-id: 6cd3eabe-067f-4e80-b17f-561290499261
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---

# Panoramica di [!DNL Quality Patches Tool] (QPT) v1.0.8

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.0.8.

QPT v1.0.8 include le seguenti patch:

1. **MDVA-28357**: sostituisce l&#39;analizzatore standard con un analizzatore personalizzato con un tokenizzatore di parole chiave per il campo SKU nell&#39;indice [!DNL ElasticSearch] per consentire il funzionamento delle query di ricerca con caratteri jolly con SKU contenenti un trattino (&quot;-&quot;).
1. **MDVA-29954**: è stato risolto il problema che causava l&#39;invio di *New Company Registration Request* e *You&#39;ve been linked to a company* email da un indirizzo errato.
1. **MDVA-30112**: è stato risolto il problema per cui se il numero di ordini supera il valore *bunch-size*, Adobe Commerce considera incoerenze gli ordini con stato *pending*.
1. **MDVA-30963**: è stato risolto il problema per cui i risultati del filtro dei prodotti impostati in modo da contenere solo i valori specificati per *Tutte le visualizzazioni archivio* nell&#39;ambito Amministratore, includi i prodotti con valori sostituiti a livello di visualizzazione archivio.
1. **MDVA-31150**: è stato risolto il problema che impediva la restituzione dei saldi delle carte regalo e di credito dello store da parte della chiamata API Rest fattura GET, quando la fattura era stata registrata da una chiamata API Rest e l&#39;ordine era stato parzialmente pagato dai conti carte regalo e di credito dello store.
1. **MDVA-31242**: è stato risolto il problema relativo alla visualizzazione di un segno di valuta errato nella griglia [!UICONTROL Credit Memo].
1. **MDVA-31295**: risolve il problema per cui i punti premio non vengono calcolati quando viene completato un ordine parziale e gli elementi vengono tassati.

Utilizza il menu a sinistra per passare a una pagina patch specifica.
