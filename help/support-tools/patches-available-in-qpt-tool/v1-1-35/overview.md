---
title: '"Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.35'''
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.35.
feature: Tools and External Services
role: Admin
exl-id: 46228690-44ce-462f-b700-1aea6fa0eeab
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.35

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.35.

QPT v1.1.35 include le seguenti patch:

1. **ACSD-51899**: risolve il problema per cui l’indirizzo di spedizione predefinito nella fase di spedizione per il pagamento viene popolato automaticamente con un indirizzo di prelievo nel negozio selezionato in precedenza.
1. **ACSD-52041**: risolve il problema relativo al messaggio di errore: *[ERRORE] [!DNL Page Builder] ha eseguito il rendering per 5 secondi senza rilasciare blocchi*. viene visualizzato in [!DNL Chrome] browser durante il salvataggio del contenuto modificato con [!DNL Page Builder].
1. **ACSD-52095**: risolve il problema relativo alla presenza di `manage_stock` il valore veniva erroneamente impostato su 0 nel file CSV dopo l’esportazione del prodotto.
1. **ACSD-51358**: risolve il problema per cui la rimozione di un aggiornamento pianificato senza una data di fine determina la rimozione di altri aggiornamenti pianificati per la stessa entità.
1. **ACSD-48070**: risolve il problema per il quale la modifica di un aggiornamento pianificato attivava un’eccezione.
1. **ACSD-51890**: risolve il problema relativo alla presenza di [!UICONTROL Submit review] può essere cliccato più volte senza [!DNL Google] Convalida di reCAPTCHA v3.
1. **ACSD-51984**: risolve il problema se non è selezionato *Usa valori predefiniti e valori dei campi prodotto non predefiniti* non vengono salvati per la seconda visualizzazione del sito Web, dello store e dello store.
1. **ACSD-52398**: corregge l’errore *La quantità richiesta non è disponibile* ciò si verifica quando si tenta di aggiornare la quantità di un prodotto nel carrello nella vetrina.
1. **ACSD-52786**: risolve il problema in cui uno SKU della regola del catalogo viene applicato a tutti i prodotti che iniziano con lo SKU specificato.
1. **ACSD-52921**: è stato risolto il problema che si verificava in caso di errore interno durante la richiesta dei dettagli del carrello a GraphQL in presenza di un prodotto configurabile esaurito nel carrello.
1. **ACSD-51683**: risolve il problema che impediva l’aggiunta di un’opzione personalizzabile al carrello tramite GraphQL.
1. **ACSD-52133**: risolve il problema che impediva il salvataggio di un account cliente dopo un aggiornamento.
1. **ACSD-52202**: risolve il problema per cui la quantità vendibile delle scorte predefinite viene erroneamente impostata su 0 quando una scorta non predefinita viene modificata in 0 qtà all&#39;evasione dell&#39;ordine.
1. **ACSD-51265**: risolve il problema con `catalog_product_price` prestazioni di reindicizzazione quando nel sistema sono presenti troppi prodotti in bundle.
1. **ACSD-52831**: risolve il problema che impediva ai clienti di inserire ordini di preventivo negoziabili quando [!DNL Google reCAPTCHA v3 Invisible] è abilitato.
1. **ACSD-51845**: risolve il problema che impediva l’aggiornamento in blocco asincrono dell’API REST di prodotti successivi con prezzi di livello e set di attributi diversi.
1. **ACSD-52815**: risolve il problema per cui l’input per il campo quantità di un’origine non predefinita supporta solo un massimo di 6 cifre, a differenza di 8 per una scorta predefinita.
1. **ACSD-51149**: risolve il problema in cui [!UICONTROL Scheduled ImportExport] con abilitato [!UICONTROL Catalog Permissions] invalida gli indicizzatori e quindi esegue il flushing della cache in base a cron.
1. **ACSD-50815**: risolve il problema che impediva l’utilizzo della quantità decimale per un prodotto semplice per una nuova opzione di prodotto nel pacchetto.
1. **ACSD-52399**: risolve il problema relativo alla visualizzazione dell’opzione del prodotto configurabile con una quantità vendibile pari a 0 *In magazzino* sulla pagina del prodotto.

Utilizza il menu a sinistra per passare a una pagina patch specifica.
