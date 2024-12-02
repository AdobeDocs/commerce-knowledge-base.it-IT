---
title: Diagnosi delle discrepanze nei ricavi di Google eCommerce
description: 'Questo articolo fornisce soluzioni per le discrepanze tra Google e Magenti Business Intelligence (MBI). Il tracciamento eCommerce di Google porta potenza sia al tuo account Google Analytics che ai dashboard di MBI, ma si traduce in molti clienti che ci chiedono: Dovrebbero entrambi gli strumenti segnalare la stessa quantità di **ordini** e **ricavi**?'
exl-id: b2e43e70-d234-4338-ae81-fa401416be5a
feature: Commerce Intelligence
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '617'
ht-degree: 0%

---

# Diagnosi delle discrepanze nei ricavi di Google eCommerce

Questo articolo fornisce soluzioni per le discrepanze tra Google e Magenti Business Intelligence (MBI). Il tracciamento di Google eCommerce porta energia sia all&#39;account Google Analytics che alle dashboard di MBI, ma molti clienti ci chiedono: entrambi gli strumenti dovrebbero riportare lo stesso importo di **ordini** e **ricavi**?

Nella nostra esperienza, la risposta è &quot;no&quot; in quasi tutti i casi. Questo perché il tracciamento di Google eCommerce ottiene le informazioni sull’ordine durante un evento di clic sul pulsante sul sito web, che non rispetta molti attributi dell’ordine registrati successivamente nel database, dagli ordini non registrati a quelli annullati o rimborsati in un secondo momento.

Sappiamo che una discrepanza tra Google e MBI può causare incertezza per te e il tuo team. Desideriamo aiutarti a capire la differenza tra questi due numeri, che potrebbe rivelare le modifiche da apportare al tuo account o database Google.

## Perché GA riporta **meno** ricavi rispetto al mio database?

Quando la funzione Google Analytics riporta in difetto gli ordini e i ricavi, ciò indica che non sta acquisendo tutti gli ordini effettuati sul sito. Poiché si è certi che i dati del database rappresentano il numero definitivo, è possibile eseguire alcuni passaggi per cercare di determinare la causa principale e, se possibile, aiutare Google a acquisire ulteriori informazioni.

* Il tracciamento eCommerce di Google non è sempre stato abilitato. Prova a esaminare un periodo più piccolo e più recente.
* Il tracciamento di Google eCommerce non è configurato per acquisire acquisti da determinati browser, sistemi operativi o dispositivi.
* L’evento di clic associato al tracciamento di Google eCommerce non tiene correttamente traccia di imposte, spese di spedizione o altre spese oltre il totale dell’ordine.
* Il timestamp del database si trova in un fuso orario diverso da quello delle Google Analytics.
* Le persone possono visitare il tuo sito tramite finestre in incognito o con i cookie disattivati.

## Perché GA riporta **più** ricavi rispetto al mio database?

Abbiamo scoperto che è più comune per le Google Analytics segnalare ordini e ricavi in eccesso rispetto a un database di eCommerce. Questo non è sempre una brutta cosa. Il tuo database è il record definitivo delle transazioni effettuate sul tuo sito web e ci sono diversi motivi per cui Google potrebbe riportare un numero elevato anche quando lo hai configurato perfettamente:

* Il tracciamento di eCommerce acquisisce i clic del pulsante duplicato che si registrano solo come un singolo ordine nel database.
* Hai un numero elevato di ordini annullati, rimborsati o fraudolenti, che è una modifica dello stato che si verifica dopo che eCommerce tiene traccia dei dati.
* Le metriche **Ricavi** e **Ordini** escludono deliberatamente gli ordini di test o interni, che Google non è in grado di differenziare.
* Gli ordini non vengono inseriti nel database in determinate circostanze.
* Il tracciamento di Google eCommerce non è a conoscenza di coupon e sconti sull’ordine.
* Il timestamp del database si trova in un fuso orario diverso da quello delle Google Analytics.

Tieni presente che anche se Google riporta un numero di rapporti superiore a quello del tuo database, è probabile che manchino alcuni ordini per i motivi descritti nella sezione precedente.

## Risoluzione dei problemi

* Crea un clone della metrica **Ricavi** senza filtri che limitino il risultato. I filtri Ordini che contiamo o Clienti che contiamo sono importanti, ma Google non ha un filtro equivalente.
* Controlla un piccolo periodo recente, ad esempio un intervallo di alcune ore all’inizio di questa settimana.
* Dopo aver configurato il tracciamento di Google eCommerce in MBI, utilizza Filtro o Raggruppamento per controllare un singolo Source, Medium o Campaign. Quindi fai lo stesso in Google. Una fonte con meno traffico/entrate sarà migliore, in quanto è come avere meno margine di errore.
