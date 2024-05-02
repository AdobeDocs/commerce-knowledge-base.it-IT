---
title: '"Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.39'''
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.39.
feature: Tools and External Services
role: Admin, Developer
exl-id: 48563701-0fa0-4c88-943e-78b421b806b5
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.39

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.39.

QPT v1.1.39 include le seguenti patch:

1. **ACSD-53704**: risolve il problema relativo al calcolo errato della cronologia del saldo dei punti di premio dopo la scadenza dei punti di premio.
1. **ACSD-53583**: migliora le prestazioni di reindicizzazione parziale per *Categoria Prodotti* e *Categorie di prodotti* indici.
1. **ACSD-54026**: corregge un messaggio di errore errato per un `updateCompanyRole` Richiesta GraphQL per un utente non autorizzato.
1. **ACSD-54106**: risolve il problema relativo all’ordinamento dei prodotti di categoria in base al nome per i caratteri accentati turchi.
1. **ACSD-52219**: è stato risolto il problema che causava il mancato funzionamento previsto dei filtri salvati dalle griglie di amministrazione quando si passava spesso da una visualizzazione all’altra come segnalibro.
1. **ACSD-54342**: corregge un messaggio di errore errato *Errore nella struttura dati: valori misti* quando si importa un file CSV senza dati validi.
1. **ACSD-54660**: aggiunto un nuovo attributo di input *sort* per ordinare gli ordini dei clienti in GraphQL per `sort_field` e `sort_direction`.
1. **ACSD-54776**: risolve il problema se non è selezionato *[!UICONTROL Use Default Value]* e i valori dei campi prodotto non predefiniti non vengono salvati per la seconda visualizzazione sito Web, store e store.
1. **ACSD-53998**: risolve il problema relativo a una **[!UICONTROL Dynamic Block]** in base a **[!UICONTROL Customer Segment]** non funziona correttamente dopo la disconnessione da un account cliente.
1. **ACSD-53204**: Correzioni *Impossibile salvare il prodotto.* errore durante l’esecuzione di richieste simultanee di aggiunta di immagini alla galleria di prodotti utilizzando `rest/V1/products/<sku>/media` endpoint.
1. **ACSD-47657**: aggiunto un meccanismo di memorizzazione in cache per le credenziali di AWS. Un provider di credenziali ora utilizza la cache del Magento per memorizzare nella cache le credenziali recuperate da AWS per la configurazione EC2.

Utilizza il menu a sinistra per passare a una pagina patch specifica.
