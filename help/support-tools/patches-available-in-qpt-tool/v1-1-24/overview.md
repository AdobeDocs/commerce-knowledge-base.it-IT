---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.24'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in  [!DNL Quality Patches Tool] (QPT) v1.1.24.
exl-id: 7c296124-c9ae-4b7c-b711-fc39741cabe2
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# Panoramica di [!DNL Quality Patches Tool] (QPT) v1.1.24

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.24.

QPT v1.1.24 include le seguenti patch:

1. **ACSD-45168**: è stato risolto il problema che impediva la generazione di URL compatibili con SEO per i prodotti con attributi *url_key* sostituiti a livello di visualizzazione archivio.
1. **ACSD-46617**: è stato risolto il problema che causava la disattivazione del pulsante **[!UICONTROL Continue to Checkout]** anche se il subtotale era maggiore dell&#39;*importo ordine minimo* configurato.
1. **ACSD-46770**: risolve il problema per cui le e-mail dell&#39;ordine amministratore vengono inviate anche quando la *conferma dell&#39;ordine e-mail* non è selezionata.
1. **ACSD-46865**: è stato risolto il problema che impediva il popolamento della griglia [!UICONTROL Shipment and Credit Memo] quando era abilitata l&#39;indicizzazione asincrona.
1. **ACSD-47004**: risolve il problema per cui l&#39;IVA non viene applicata a un indirizzo di fatturazione senza un ID IVA.
1. **ACSD-47079**: risolve il problema per cui lo stato delle scorte dei prodotti compositi (bundle, raggruppati e configurabili) non viene aggiornato quando lo stato delle scorte dei prodotti secondari cambia tramite REST API POST /rest/V1/inventory/source-items.
1. **ACSD-47137**: migliora la velocità di caricamento della raccolta immagini quando la cartella pub/media è molto grande.
1. **ACSD-47336**: Correzioni di *Si è verificato un errore.* errore durante l&#39;eliminazione delle notifiche nell&#39;amministrazione di Commerce.
1. **ACSD-47559**: è stato corretto il problema per cui l&#39;area Anteprima modello e-mail non era completamente visibile.
1. **ACSD-47803**: è stato risolto il problema che causava la visualizzazione dei campioni di prodotto configurabili esauriti come disponibili.
1. **ACSD-47920**: è stato risolto il problema che consentiva di effettuare gli ordini tramite l&#39;API REST come utente guest anche quando *Consenti estrazione guest* è disattivato.
1. **ACSD-47955**: è stato risolto il problema che impediva la corretta visualizzazione dello sconto sul carrello in GraphQL.

Utilizza il menu a sinistra per passare a una pagina patch specifica.
