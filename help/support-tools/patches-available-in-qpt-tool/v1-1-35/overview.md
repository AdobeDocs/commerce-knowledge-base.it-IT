---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.35'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in  [!DNL Quality Patches Tool] (QPT) v1.1.35.
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

1. **ACSD-51899**: è stato risolto il problema che causava la compilazione automatica dell&#39;indirizzo di spedizione predefinito nella fase di spedizione di pagamento con un indirizzo di prelievo in-store selezionato in precedenza.
1. **ACSD-52041**: è stato risolto il problema relativo al rendering del messaggio di errore *[ERROR] [!DNL Page Builder] per 5 secondi senza rilasciare blocchi*. viene visualizzato nel browser [!DNL Chrome] quando si salva il contenuto modificato con [!DNL Page Builder].
1. **ACSD-52095**: è stato corretto il problema a causa del quale il valore `manage_stock` veniva erroneamente impostato su 0 nel file CSV dopo l&#39;esportazione del prodotto.
1. **ACSD-51358**: è stato risolto il problema che causava la rimozione di un aggiornamento pianificato senza data di fine, con la conseguente rimozione di altri aggiornamenti pianificati per la stessa entità.
1. **ACSD-48070**: è stato risolto il problema che causava l&#39;eccezione durante la modifica di un aggiornamento pianificato.
1. **ACSD-51890**: è stato risolto il problema per cui è possibile fare clic più volte sul pulsante [!UICONTROL Submit review] senza la convalida di [!DNL Google] reCAPTCHA v3.
1. **ACSD-51984**: è stato risolto il problema che impediva il salvataggio dei valori dei campi *Usa valore predefinito e non predefinito* non selezionati per il secondo sito Web, archivio e visualizzazione archivio.
1. **ACSD-52398**: è stato corretto l&#39;errore *La quantità richiesta non è disponibile* che si verifica quando si tenta di aggiornare la quantità di un prodotto nel carrello nella vetrina.
1. **ACSD-52786**: risolve il problema relativo all&#39;applicazione di uno SKU della regola catalogo a tutti i prodotti che iniziano con lo SKU specificato.
1. **ACSD-52921**: è stato risolto il problema che si verificava in presenza di un errore interno durante la richiesta dei dettagli del carrello a GraphQL quando nel carrello era presente un prodotto configurabile esaurito.
1. **ACSD-51683**: è stato risolto il problema che impediva l&#39;aggiunta di un&#39;opzione personalizzabile al carrello tramite GraphQL.
1. **ACSD-52133**: è stato risolto il problema che impediva il salvataggio di un account cliente dopo un aggiornamento.
1. **ACSD-52202**: è stato risolto il problema che causava la modifica errata della quantità vendibile delle scorte predefinite in 0 quando una scorta non predefinita veniva modificata in 0 qtà all&#39;evasione dell&#39;ordine.
1. **ACSD-51265**: è stato risolto il problema relativo alle prestazioni di reindicizzazione di `catalog_product_price` quando nel sistema sono presenti troppi prodotti in bundle.
1. **ACSD-52831**: è stato risolto il problema che impediva ai clienti di inserire ordini di preventivo negoziabili quando [!DNL Google reCAPTCHA v3 Invisible] è abilitato.
1. **ACSD-51845**: è stato risolto il problema che impediva l&#39;aggiornamento dei prodotti successivi con prezzi di livello e set di attributi diversi tramite l&#39;API REST in blocco asincrona.
1. **ACSD-52815**: è stato risolto il problema per cui l&#39;input per il campo quantità di un&#39;origine non predefinita supporta solo un massimo di 6 cifre, a differenza di 8 per un titolo predefinito.
1. **ACSD-51149**: è stato corretto il problema per cui [!UICONTROL Scheduled ImportExport] con [!UICONTROL Catalog Permissions] abilitato invalida gli indicizzatori e quindi esegue il flushing della cache in base a cron.
1. **ACSD-50815**: è stato risolto il problema che impediva l&#39;utilizzo della quantità decimale per un prodotto semplice per una nuova opzione di prodotto in bundle.
1. **ACSD-52399**: è stato risolto il problema che causava la visualizzazione di *In magazzino* nella pagina del prodotto da parte dell&#39;opzione del prodotto configurabile con un valore Qtà vendibile pari a 0.

Utilizza il menu a sinistra per passare a una pagina patch specifica.
