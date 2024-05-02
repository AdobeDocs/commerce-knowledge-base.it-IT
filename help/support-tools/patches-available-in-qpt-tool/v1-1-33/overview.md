---
title: '"Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.33'''
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.33.
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

1. **ACSD-50478**: corregge il comando di rollback del database relativo a un caso in cui il dump del database contiene trigger e un comando SQL di delimitazione.
1. **ACSD-50512**: corregge l’errore: *Il collegamento scaricabile non è correlato al prodotto. Verifica il collegamento e riprova.*  ciò si verifica quando si aggiorna la data di inizio di un aggiornamento scaricabile della gestione temporanea del prodotto.
1. **ACSD-50949**: risolve il problema relativo alla presenza del filtro del prezzo in [!UICONTROL Advanced Search] non restituisce risultati corretti se utilizzato lungo il filtro SKU.
1. **ACSD-51645**: corregge l’errore generato durante il salvataggio di una nuova [!UICONTROL Cart Price Rule] se l&#39;estensione `Magento_OfflineShipping` è disabilitato.
1. **ACSD-50895**: risolve il problema in cui [!DNL Google Analytics] 3 I tag GTM non vengono attivati se [!DNL Google Analytics] 4 GTM non è configurato.
1. **ACSD-51102**: corregge il problema per cui una regola di catalogo applicata a un numero elevato di prodotti non viene indicizzata correttamente quando la regola è abilitata da un aggiornamento pianificato.
1. **ACSD-50368**: risolve il problema relativo alla `group_id` viene ignorato quando un cliente viene creato tramite Async REST API o Async Bulk REST API.
1. **ACSD-51497**: risolve il problema per cui un cliente non può ordinare una pagina di catalogo per [!UICONTROL Custom Attribute] del tipo a discesa.
1. **ACSD-51408**: corregge il problema relativo all’errata impostazione dello stato dell’elemento dell’ordine su [!UICONTROL Backordered].
1. **ACSD-51735**: corregge il problema relativo all’errata impostazione dello stato dell’elemento dell’ordine su [!UICONTROL Ordered] quando lo stock del prodotto è *0*.
1. **ACSD-51792**: risolve il problema se una pagina non ha l’evento di impression quando [!DNL Google Tag Manager] 4 è attivato.
1. **ACSD-51471**: risolve il problema che impediva a un utente amministratore di salvare un aggiornamento pianificato per un prodotto in bundle che utilizza un prodotto semplice con un aggiornamento pianificato.
1. **ACSD-51700**: corregge l’errore che si verifica quando si passa da una visualizzazione archivio a un’altra in una pagina di modifica del prodotto scaricabile nell’amministratore.
1. **ACSD-51120**: è stato corretto il problema per cui la cache delle richieste di GraphQL GET non veniva cancellata per le pagine CMS che contenevano blocchi CMS aggiornati tramite un aggiornamento di staging.
1. **ACSD-51240**: risolve il problema relativo alla mancanza del file caricato se la registrazione viene effettuata tramite il modulo di registrazione della società.
1. **ACSD-51907**: risolve il problema che impediva a un utente amministratore con restrizioni di creare una nota di credito con un rimborso offline.
1. **ACSD-52148**: risolve il problema relativo alla presenza di [!UICONTROL Google V3 reCAPTCHA Admin] l’accesso a volte non riesce.
1. **ACSD-51431**: risolve il problema relativo al funzionamento dello stato di un indicizzatore anche se non sono presenti nuove voci nel changelog.
1. **ACSD-51892**: è stato risolto il problema di prestazioni che si verificava quando i file di configurazione venivano caricati più volte durante la distribuzione.

Utilizza il menu a sinistra per passare a una pagina patch specifica.
