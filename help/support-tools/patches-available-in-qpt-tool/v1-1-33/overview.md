---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.33'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in  [!DNL Quality Patches Tool] (QPT) v1.1.33.
feature: Tools and External Services
role: Admin
exl-id: df3ae5e2-7c57-4ccd-af34-eb78cc60bcf6
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.33

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.33.

QPT v1.1.33 include le seguenti patch:

1. **ACSD-50478**: corregge il comando di rollback del database per un caso in cui il dump del database contiene trigger e un comando SQL delimitatore.
1. **ACSD-50512**: è stato corretto l&#39;errore: *Il collegamento scaricabile non è correlato al prodotto. Verifica il collegamento e riprova.* che si verifica quando si aggiorna la data di inizio per un aggiornamento scaricabile della gestione temporanea del prodotto.
1. **ACSD-50949**: è stato risolto il problema che impediva al filtro prezzi in [!UICONTROL Advanced Search] di restituire risultati corretti se utilizzato insieme al filtro SKU.
1. **ACSD-51645**: corregge l&#39;errore generato durante il salvataggio di un nuovo [!UICONTROL Cart Price Rule] se l&#39;estensione `Magento_OfflineShipping` è disabilitata.
1. **ACSD-50895**: è stato corretto il problema per cui [!DNL Google Analytics] 3 tag GTM non vengono attivati se [!DNL Google Analytics] 4 GTM non è configurato.
1. **ACSD-51102**: è stato risolto il problema che impediva la corretta indicizzazione di una regola di catalogo applicata a un numero elevato di prodotti quando la regola veniva abilitata da un aggiornamento pianificato.
1. **ACSD-50368**: è stato risolto il problema per cui `group_id` del cliente viene ignorato quando viene creato un cliente tramite API REST asincrona o API REST asincrona di massa.
1. **ACSD-51497**: è stato risolto il problema che impediva a un cliente di ordinare una pagina di catalogo in base a [!UICONTROL Custom Attribute] del tipo a discesa.
1. **ACSD-51408**: è stato corretto il problema a causa del quale lo stato dell&#39;elemento dell&#39;ordine non è impostato correttamente su [!UICONTROL Backordered].
1. **ACSD-51735**: è stato corretto il problema a causa del quale lo stato dell&#39;elemento dell&#39;ordine non è impostato correttamente su [!UICONTROL Ordered] quando le scorte del prodotto sono *0*.
1. **ACSD-51792**: è stato corretto il problema per cui una pagina non presenta l&#39;evento di impression quando [!DNL Google Tag Manager] 4 è abilitato.
1. **ACSD-51471**: è stato risolto il problema che impediva a un utente amministratore di salvare un aggiornamento pianificato per un prodotto in bundle che utilizza un prodotto semplice con un aggiornamento pianificato.
1. **ACSD-51700**: è stato corretto l&#39;errore che si verificava quando si cambiavano le visualizzazioni dello store in una pagina di modifica del prodotto scaricabile nell&#39;amministratore.
1. **ACSD-51120**: è stato corretto il problema per cui la cache delle richieste di GraphQL GET non viene cancellata per le pagine CMS che contengono blocchi CMS aggiornati tramite un aggiornamento di staging.
1. **ACSD-51240**: è stato corretto il problema di mancanza del file caricato se la registrazione viene effettuata tramite il modulo di registrazione della società.
1. **ACSD-51907**: è stato risolto il problema che impediva a un utente amministratore con restrizioni di creare una nota di credito con rimborso offline.
1. **ACSD-52148**: è stato risolto il problema che causava errori occasionali nell&#39;accesso a [!UICONTROL Google V3 reCAPTCHA Admin].
1. **ACSD-51431**: risolve il problema relativo al funzionamento dello stato di un indicizzatore anche se non sono presenti nuove voci nel changelog.
1. **ACSD-51892**: è stato risolto il problema di prestazioni che si verificava quando i file di configurazione venivano caricati più volte durante la distribuzione.

Utilizza il menu a sinistra per passare a una pagina patch specifica.
