---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.48'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in  [!DNL Quality Patches Tool] (QPT) v1.1.48.
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

1. **ACSD-55566**: è stato risolto il problema che impediva l&#39;esecuzione di *[!UICONTROL mergeCart mutation]* con un *Errore interno del server* nella risposta di GraphQL durante l&#39;unione di carrelli di origine e di destinazione contenenti gli stessi elementi inclusi nel bundle.
1. **ACSD-56546**: è stato risolto il problema che causava la visualizzazione dei prodotti configurabili e in bundle come *[!UICONTROL Out of Stock]* nella vetrina quando la configurazione *[!UICONTROL Display Out of Stock Product]* era disabilitata.
1. **ACSD-56635**: è stato corretto il problema per cui il cliente importato viene duplicato con lo stesso indirizzo e-mail quando si utilizza l&#39;importazione con [!UICONTROL Account Sharing] impostato su *[!UICONTROL Global]*.
1. **ACSD-56741**: è stato corretto il messaggio di errore *Tentativo di accedere all&#39;offset dell&#39;array sul valore di tipo null* visualizzato durante `setup:upgrade` quando il database contiene un trigger MySQL personalizzato non correlato al meccanismo di indicizzazione e [!DNL MView].
1. **ACSD-57315**: è stato risolto il problema relativo alla creazione di una nuova transazione in [!DNL PayPal Payflow Pro] ogni volta che si fa clic sul pulsante **[!UICONTROL Fetch]** nella schermata Visualizza transazione in [!UICONTROL Admin].
1. **ACSD-57337**: è stato risolto il problema che consentiva a un utente amministratore con restrizioni di accesso a siti Web specifici di visualizzare le società di tutti i siti Web nella griglia *[!UICONTROL Companies]*.
1. **ACSD-57394**: corregge l&#39;ordinamento errato dei prodotti in base a più campi di ordinamento in GraphQL.
1. **ACSD-57565**: è stato risolto il problema che causava la visualizzazione di informazioni sull&#39;ordine errate nel dashboard *[!UICONTROL Order]* fino all&#39;aggiornamento del periodo di tempo. Il dashboard visualizza ora le statistiche corrette dell’ordine al primo caricamento.
1. **ACSD-57854**: è stato risolto il problema che determinava la restituzione da parte delle richieste GraphQL dei prodotti di categorie disabilitate nelle aggregazioni di categorie.
1. **ACSD-58008**: è stato risolto il problema per cui l&#39;aggiornamento pianificato rimuove la versione precedente dell&#39;elemento nell&#39;area intermedia se non è specificata una data di fine.

Utilizza il menu a sinistra per passare a una pagina patch specifica.

