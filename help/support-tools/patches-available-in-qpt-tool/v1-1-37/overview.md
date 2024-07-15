---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.37'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in  [!DNL Quality Patches Tool] (QPT) v1.1.37.
feature: Tools and External Services
role: Admin, Developer
exl-id: 4ccdba38-8171-4cc4-b8ef-d2c53dec0b47
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.37

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.37.

QPT v1.1.37 include le seguenti patch:

1. **ACSD-52613**: è stato risolto il problema che causava l&#39;aggiornamento delle cache e degli indici anche quando non venivano effettuati aggiornamenti a `Inventory_source` elementi da parte dell&#39;API rest.
1. **ACSD-51884**: è stato risolto il problema che causava la correzione del percorso della cache delle immagini del prodotto dopo l&#39;esecuzione del comando di ridimensionamento.
1. **ACSD-53628**: è stato risolto il problema che causava la visualizzazione di caratteri speciali non corretti nel report ordine cliente CSV.
1. **ACSD-49843**: è stato risolto il problema che impediva la disponibilità del collegamento al download del prodotto dopo la fatturazione automatica dell&#39;articolo ordinato tramite metodo di pagamento online con l&#39;impostazione *[!UICONTROL Payment Action]* = *[!UICONTROL Sale]* abilitata.
1. **ACSD-53148**: è stato corretto il problema per cui due richieste parallele in GraphQL per l&#39;aggiunta dello stesso prodotto configurabile al carrello causavano due elementi separati sul carrello con lo stesso SKU prodotto.
1. **ACSD-47054**: è stato risolto il problema che causava la reindicizzazione dell&#39;anteprima in tutti gli archivi, causando rallentamenti.
1. **ACSD-52606**: è stato risolto il problema relativo al messaggio di errore *Quando l&#39;utente fa clic su **[!UICONTROL Notify Order is Ready for Pickup]**, l&#39;ordine non è pronto per il ritiro*.
1. **ACSD-51574**: è stato risolto il problema che impediva l&#39;aggiornamento dell&#39;immagine sul front-end dopo la sua sostituzione con un&#39;altra immagine con lo stesso nome.
1. **ACSD-53728**: è stato risolto il problema che causava il ritardo nel completamento dell&#39;indicizzatore EAV del prodotto.
1. **ACSD-53979**: risolve il problema JS che si verifica nella home page se il messaggio di benvenuto contiene una virgoletta singola.
1. **ACSD-52143**: è stato risolto il problema che determinava la rimozione delle opzioni personalizzate dopo l&#39;importazione del prodotto.
1. **ACSD-53750**: è stato corretto l&#39;errore *Connessione interrotta o chiusa* durante la reindicizzazione `catalog_product_price` multithread.

Utilizza il menu a sinistra per passare a una pagina patch specifica.
