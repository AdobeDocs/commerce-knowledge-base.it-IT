---
title: Arresto anomalo del servizio Redis
description: L’articolo consiglia come correggere Redis.
exl-id: 5eb8fb70-0f41-433a-8d3f-c368781a2d1d
feature: Services
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---

# Arresto anomalo del servizio Redis

L’articolo consiglia come correggere Redis.

## Prodotti e versioni interessati

* Adobe Commerce sull’infrastruttura cloud 2.2.x., 2.3.x
* Adobe Commerce on-premise 2.2.x., 2.3x
* Tutte le versioni di Redis

## Problema

Rallentamento o interruzione del sito web a causa di overflow della memoria in Redis.

## Causa

L’overflow della memoria può causare l’arresto anomalo del servizio Redis. Durante il periodo di picco, il servizio Redis potrebbe richiedere una quantità di memoria superiore a quella attualmente allocata.

## Soluzione

Per verificare la configurazione corrente e la memoria utilizzata, eseguire il comando seguente in CLI. Verifica la memoria utilizzata, la memoria massima, le chiavi eliminate e il tempo di attività Redis in giorni:

```
redis-cli -p REDIS_PORT -h REDIS_HOST info | egrep --color "(role|used_memory_peak|maxmemory|evicted_keys|uptime_in_days)"
```

Il *REDIS\_PORT* e *REDIS\_HOST* le variabili possono essere recuperate da `app/etc/env.php`.

Se l&#39;output dell&#39;esecuzione della query precedente indica che la percentuale di memoria disponibile è inferiore al 40%, [invia un ticket al supporto Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) chiedere un aumento del `maxmemory` in Redis Server. Se il valore delle chiavi eliminate non è &quot;0&quot; o il tempo di attività Redis in giorni è uguale a 0 (indicando che Redis si è bloccato oggi), devi anche [invia un ticket al supporto Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) richiesta di un&#39;indagine e di una correzione per il problema.

## Lettura correlata

Per ulteriori informazioni sulla memoria Redis, fare riferimento a [Ottimizzazione della memoria Redis](https://redis.io/topics/memory-optimization).
