---
title: '"Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.48'''
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.48.
feature: Tools and External Services
role: Admin, Developer
exl-id: 6170c616-312c-4de3-98dc-e2c27c376608
source-git-commit: 42712af2ce4337cd64b8dea555139e4252fb91cf
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.48

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.48.

QPT v1.1.48 include le seguenti patch:

1. **ACSD-55566**: risolve il problema relativo alla presenza di *[!UICONTROL mergeCart mutation]* non riesce con un *Errore interno del server* nella risposta di GraphQL durante l’unione dei carrelli di origine e di destinazione sono presenti gli stessi elementi in bundle.
1. **ACSD-56546**: risolve il problema relativo alla visualizzazione dei prodotti configurabili e in bundle con *[!UICONTROL Out of Stock]* nella vetrina quando *[!UICONTROL Display Out of Stock Product]* la configurazione è disabilitata.
1. **ACSD-56635**: risolve il problema in cui il cliente importato viene duplicato con lo stesso indirizzo e-mail quando si utilizza l’importazione con [!UICONTROL Account Sharing] imposta su *[!UICONTROL Global]*.
1. **ACSD-56741**: corregge il messaggio di errore *Tentativo di accedere all&#39;offset dell&#39;array su un valore di tipo null* che viene visualizzato durante `setup:upgrade` quando il database contiene un trigger MySQL personalizzato non correlato al meccanismo di indicizzazione e [!DNL MView].
1. **ACSD-57315**: risolve il problema relativo alla creazione di una nuova transazione in [!DNL PayPal Payflow Pro] ogni volta che **[!UICONTROL Fetch]** nella schermata visualizza transazione in [!UICONTROL Admin].
1. **ACSD-57337**: risolve il problema per cui un utente amministratore con restrizioni di accesso a siti web specifici può visualizzare le aziende di tutti i siti web in *[!UICONTROL Companies]* griglia.
1. **ACSD-57394**: corregge l’ordinamento errato dei prodotti in base a più campi di ordinamento in GraphQL.
1. **ACSD-57565**: risolve il problema relativo alla presenza di *[!UICONTROL Order]* il dashboard visualizza informazioni di ordine errate fino all’aggiornamento del periodo di tempo. Il dashboard visualizza ora le statistiche corrette dell’ordine al primo caricamento.
1. **ACSD-57854**: è stato risolto il problema che causava la restituzione da parte delle richieste di prodotti GraphQL di categorie disabilitate nelle aggregazioni di categorie.
1. **ACSD-58008**: risolve il problema per cui l’aggiornamento pianificato rimuove la versione precedente dell’elemento nell’area intermedia se non viene specificata una data di fine.

Utilizza il menu a sinistra per passare a una pagina patch specifica.

