---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.50'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in  [!DNL Quality Patches Tool] (QPT) v1.1.50.
feature: Tools and External Services
role: Admin, Developer
source-git-commit: f62cf4284d7bb99a1ab58df676dfff726c34d327
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.50

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.50.

QPT v1.1.50 include le seguenti patch:

1. **ACSD-59280**: è stato risolto il problema che si verificava quando si installavano le versioni 2.4.4-pX del metodo *Call to undefined ReflectionUnionType::getName()*.
1. **ACSD-45049**: è stato risolto il problema che impediva il corretto funzionamento dell&#39;impostazione dell&#39;attributo del cliente *[!UICONTROL Is required]* in base all&#39;ambito del sito Web in Amministrazione.
1. **ACSD-46938**: è stato risolto il problema relativo alle prestazioni della ricreazione dei trigger del database durante `setup:upgrade`.
1. **ACSD-48210**: è stato risolto il problema per cui l&#39;aggiornamento dell&#39;attributo *[!UICONTROL website scope]* in una visualizzazione archivio specifica sostituisce i valori dell&#39;attributo nell&#39;ambito globale.
1. **ACSD-54887**: è stato risolto il problema che causava l&#39;eliminazione del carrello acquisti del cliente dopo la scadenza della sessione con *[!UICONTROL Persistent Shopping Cart]* abilitato.
1. **ACSD-58141**: è stato risolto il problema che causava la rigenerazione di `PHPSESSID` nelle richieste POST nell&#39;area di vetrina per un cliente connesso se [!UICONTROL L2 Redis cache] era abilitato e il cliente veniva aggiornato dall&#39;amministratore.
1. **ACSD-58352**: è stato risolto il problema per cui le etichette degli attributi restituiti per la visualizzazione archivio predefinita vengono restituite tramite API GraphQL quando nell&#39;intestazione della richiesta è specificata una visualizzazione archivio non predefinita.
1. **ACSD-58442**: è stato risolto il problema che causava il caricamento del menu e dell&#39;intestazione in una visualizzazione per dispositivi mobili anziché desktop con una larghezza di *768px*.
1. **ACSD-58790**: è stata corretta la funzionalità *pinch-to-zoom* nelle immagini della pagina dei dettagli del prodotto nella visualizzazione per dispositivi mobili in [!DNL Chrome].
1. **ACSD-59036**: è stata corretta un&#39;eccezione che si verifica quando si caricano i prezzi dei prodotti con limiti inferiore e superiore uguali a *$0*.
1. **ACSD-59229**: è stato risolto il problema che causava il salvataggio delle informazioni relative al gruppo di clienti nel segmento errato a causa del valore precedente di [!UICONTROL X-Magento-Vary] nella richiesta.
1. **ACSD-59378**: è stato corretto il problema di aggiornamento errato delle riscritture URL a livello di archivio durante l&#39;importazione.
1. **ACSD-59514**: è stato corretto il problema a causa del quale i moduli nell&#39;area di amministrazione con [!DNL Page Builder] generavano il rendering di *[!DNL Page Builder]per 5 secondi senza rilasciare blocchi.Errore* nella console del browser dopo l&#39;invio del modulo e le modifiche non possono essere salvate.
1. **ACSD-60303**: è stato risolto il problema che impediva di effettuare un ordine da Amministratore se era abilitata la minimizzazione HTML.
1. **ACSD-60441**: è stato risolto il problema relativo all&#39;aggiornamento dei clienti tramite l&#39;endpoint `V1/customers REST API` quando si utilizza il token di accesso all&#39;integrazione generato dal back-end.

Utilizza il menu a sinistra per passare a una pagina patch specifica.

