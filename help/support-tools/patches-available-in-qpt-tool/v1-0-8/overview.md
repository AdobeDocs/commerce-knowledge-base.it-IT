---
title: '"Panoramica: [!DNL Quality Patches Tool] (QPT) v1.0.8'''
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.0.8.
exl-id: 6cd3eabe-067f-4e80-b17f-561290499261
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] Panoramica di (QPT) v1.0.8

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.0.8.

QPT v1.0.8 include le seguenti patch:

1. **MDVA-28357**: sostituisce l’analizzatore standard con un analizzatore personalizzato con un tokenizzatore per parole chiave per il campo SKU in [!DNL ElasticSearch] indice per far funzionare le query di ricerca con caratteri jolly con SKU contenenti un trattino (&quot;-&quot;).
1. **MDVA-29954**: risolve il problema relativo alla presenza di *Nuova richiesta di registrazione società* e *Sei stato collegato a un’azienda* le e-mail vengono inviate dall’indirizzo errato.
1. **MDVA-30112**: risolve il problema se il numero di ordini supera il *dimensione-mazzo* valore, Adobe Commerce considera gli ordini con *in sospeso* stato come incoerenze.
1. **MDVA-30963**: risolve il problema per cui i risultati del filtro dei prodotti impostati per contenere solo i valori specificati per *Tutte le visualizzazioni dello store* in Admin, includi i prodotti con valori sostituiti a livello di visualizzazione store.
1. **MDVA-31150**: corregge il problema per cui i saldi delle carte regalo e di credito del negozio non vengono restituiti dalla chiamata API Rest fattura GET, quando la fattura è stata registrata dalla chiamata API Rest e l’ordine è stato parzialmente pagato dai conti carte regalo e di credito del negozio.
1. **MDVA-31242**: corregge il problema relativo alla visualizzazione di un simbolo di valuta errato in [!UICONTROL Credit Memo] griglia.
1. **MDVA-31295**: risolve il problema per cui i punti premio non vengono calcolati quando un ordine parziale viene completato e gli elementi vengono tassati.

Utilizza il menu a sinistra per passare a una pagina patch specifica.
