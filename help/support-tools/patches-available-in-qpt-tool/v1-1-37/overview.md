---
title: '"Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.37'''
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.37.
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

1. **ACSD-52613**: risolve il problema relativo all’aggiornamento delle cache e degli indici anche quando non vengono effettuati aggiornamenti a `Inventory_source` elementi per API rest.
1. **ACSD-51884**: risolve il problema relativo al percorso errato della cache delle immagini del prodotto dopo l’esecuzione del comando resize.
1. **ACSD-53628**: risolve il problema relativo alla visualizzazione di caratteri speciali non corretti nel rapporto CSV ordini cliente.
1. **ACSD-49843**: risolve il problema per cui il collegamento sul download del prodotto non è disponibile dopo che l’articolo ordinato è stato fatturato automaticamente tramite metodo di pagamento online con il *[!UICONTROL Payment Action]* = *[!UICONTROL Sale]* impostazione abilitata.
1. **ACSD-53148**: risolve il problema per cui due richieste parallele in GraphQL per l’aggiunta dello stesso prodotto configurabile al carrello causavano due elementi separati sul carrello con lo stesso SKU del prodotto.
1. **ACSD-47054**: risolve il problema relativo alla reindicizzazione dell’anteprima, che provoca rallentamento, se la reindicizzazione viene eseguita per tutti gli store.
1. **ACSD-52606**: corregge il problema relativo al punto in cui il messaggio di errore *Il tuo ordine non è pronto per il ritiro* viene visualizzato quando l’utente fa clic su **[!UICONTROL Notify Order is Ready for Pickup]**.
1. **ACSD-51574**: risolve il problema se l’immagine non viene aggiornata sul front-end dopo essere stata sostituita con un’altra immagine con lo stesso nome.
1. **ACSD-53728**: è stato risolto il problema che causava il ritardo nel completamento dell’indicizzatore EAV del prodotto.
1. **ACSD-53979**: risolve il problema JS che si verifica nella pagina home se il messaggio di benvenuto contiene una virgoletta singola.
1. **ACSD-52143**: risolve il problema relativo alla rimozione delle opzioni personalizzate dopo l’importazione del prodotto.
1. **ACSD-53750**: corregge il *Tubo rotto o connessione chiusa* errore durante multithreading `catalog_product_price` reindicizzare.

Utilizza il menu a sinistra per passare a una pagina patch specifica.
