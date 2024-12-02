---
title: 'Query SQL: SPIEGARE GLI ERRORI RELATIVI AI COSTI'
description: Questo articolo fornisce soluzioni per gli errori EXPLAIN cost durante l'esecuzione di query SQL non riuscite. PostgreSQL utilizza una funzione denominata [il comando EXPLAIN](https://www.postgresql.org/docs/9.5/static/using-explain.html) per determinare il costo delle query SQL. Abbiamo creato il Report Builder SQL per utilizzare anche questo comando, il che significa che se il costo viene ritenuto troppo elevato, ovvero la quantità di risorse necessarie per eseguire la query supera le soglie, la query non verrà eseguita e verrà visualizzato un messaggio EXPLAIN.
exl-id: 6f6df66a-665e-46a8-ad4c-842a0270c4eb
feature: Commerce Intelligence
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# Query SQL: SPIEGARE GLI ERRORI RELATIVI AI COSTI

Questo articolo fornisce soluzioni per gli errori EXPLAIN cost durante l&#39;esecuzione di query SQL non riuscite. PostgreSQL utilizza il comando [EXPLAIN](https://www.postgresql.org/docs/9.5/static/using-explain.html) per determinare il costo delle query SQL. Abbiamo creato il Report Builder SQL per utilizzare anche questo comando, il che significa che se il costo viene ritenuto troppo elevato, ovvero la quantità di risorse necessarie per eseguire la query supera le soglie, la query non verrà eseguita e verrà visualizzato un messaggio EXPLAIN.

Ci sono alcuni motivi per cui questo potrebbe accadere. Di seguito sono riportati i messaggi che potresti ricevere, il loro significato e come risolverli.

## Impossibile eseguire la query. Il valore di costo EXPLAIN \[xxx\] è troppo alto per eseguire questa query.

Se viene visualizzato questo messaggio, significa che l&#39;esecuzione della query è stata ritenuta troppo costosa. Abbiamo due raccomandazioni per questa situazione: una è quella di eliminare qualsiasi clausola ORDER BY dalla query, in quanto si tratta di operazioni costose. La seconda consiste nel seguire i suggerimenti contenuti nell&#39;[articolo sull&#39;ottimizzazione](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/best-practices/data/optimizing-your-sql-queries.html) per modificare la query.

## Impossibile eseguire la query. Questa query restituisce \[xxx\] righe, superando il limite di 10.000

In questo caso, il numero possibile di risultati supera il massimo impostato per il Report Builder SQL. Esistono alcuni modi per ridurre il numero di risultati:

* Prova ad aggiungere alcuni filtri alla query.
* Se possibile, utilizza LIMIT. Alcune tabelle contengono un numero elevato di righe e la limitazione dei risultati può mantenerti al di sotto del limite di righe.

## Impossibile analizzare la risposta EXPLAIN.

Ops. Questo messaggio in genere significa che qualcosa probabilmente è andato storto nel nostro caso. Se l&#39;errore persiste, contattare il supporto tecnico.
