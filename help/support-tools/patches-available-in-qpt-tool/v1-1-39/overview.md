---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.39'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in  [!DNL Quality Patches Tool] (QPT) v1.1.39.
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

1. **ACSD-53704**: risolve il problema relativo al calcolo errato della cronologia del saldo dei punti premio dopo la scadenza dei punti premio.
1. **ACSD-53583**: migliora le prestazioni di reindicizzazione parziale per *Prodotti categoria* e *Indicizzatori categorie prodotto*.
1. **ACSD-54026**: è stato corretto un messaggio di errore non corretto per una richiesta GraphQL `updateCompanyRole` per un utente non autorizzato.
1. **ACSD-54106**: è stato corretto il problema che impediva l&#39;ordinamento dei prodotti di categoria in base al nome per i caratteri accentati turchi.
1. **ACSD-52219**: è stato risolto il problema che causava il mancato funzionamento previsto dei filtri salvati dalle griglie di amministrazione quando si passava spesso da una visualizzazione a un&#39;altra.
1. **ACSD-54342**: è stato corretto un messaggio di errore non corretto *Errore nella struttura dei dati: i valori sono misti* quando si importa un file CSV senza dati validi.
1. **ACSD-54660**: aggiunto un nuovo attributo di input *sort* per ordinare gli ordini cliente in GraphQL in base a `sort_field` e `sort_direction`.
1. **ACSD-54776**: è stato risolto il problema che impediva il salvataggio dei valori non selezionati *[!UICONTROL Use Default Value]* e non predefiniti dei campi prodotto per la seconda visualizzazione sito Web, archivio e archivio.
1. **ACSD-53998**: è stato risolto il problema che impediva il corretto funzionamento di **[!UICONTROL Dynamic Block]** basato su **[!UICONTROL Customer Segment]** dopo la disconnessione da un account cliente.
1. **ACSD-53204**: correzioni *Impossibile salvare il prodotto.Errore* durante l&#39;esecuzione di richieste simultanee per l&#39;aggiunta di immagini alla raccolta prodotti utilizzando l&#39;endpoint `rest/V1/products/<sku>/media`.
1. **ACSD-47657**: aggiunto un meccanismo di caching per le credenziali di AWS. Un provider di credenziali ora utilizza la cache del Magento per memorizzare nella cache le credenziali recuperate da AWS per la configurazione EC2.

Utilizza il menu a sinistra per passare a una pagina patch specifica.
