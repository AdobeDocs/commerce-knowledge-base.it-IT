---
title: Consultate i registri per risolvere i problemi relativi agli errori 500 e 503 in Adobe Commerce
description: Questo articolo spiega come controllare il "access.log" e i relativi registri per risolvere i problemi relativi agli errori 503 e 500, che possono essere causati da traffico o risorse server insufficienti. La visualizzazione di "access.log" e dei relativi registri può fornire informazioni su ciò che potrebbe causare problemi relativi ad Adobe Commerce sull’infrastruttura cloud.
exl-id: 47d7de6b-3e12-4e79-a5c1-c27a9196b99c
feature: Cloud, Logs
source-git-commit: 66ac9de94e9a4a1eccdb5aac1875ecf0a0637e90
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# Consultate i registri per risolvere i problemi relativi agli errori 500 e 503 in Adobe Commerce

In questo articolo viene illustrato come controllare `access.log` e i registri correlati per risolvere gli errori 503 e 500, che possono essere causati da traffico o risorse server insufficienti. La visualizzazione di `access.log` e dei relativi registri può fornire informazioni su ciò che potrebbe causare problemi relativi ad Adobe Commerce sull&#39;infrastruttura cloud.

<!--
Bob - not in TOC
-->

## Prodotti e versioni interessati

* Adobe Commerce sull&#39;infrastruttura cloud, tutte le [versioni supportate](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/lifecycle-policy.html?lang=it).

Per visualizzare i registri per questi errori del server, controllare `access.log` sul server Web, ad esempio `<ip address>` `<timestamp>` `<request uri>` `<response code>` `<referer url>`

Per controllare i registri correlati:

1. Esegui il seguente comando nella CLI se si trova nel giorno corrente (per Adobe Commerce su infrastruttura cloud, architettura del piano Pro). Oppure fino a un certo punto nel passato (per Adobe Commerce sull&#39;infrastruttura cloud Architettura del piano Starter), poiché la durata della copertura dei registri è limitata e la rotazione dei registri non è disponibile: `grep -r "\" [50[0-9]" /path/to/access.log` Se l&#39;errore si è verificato nell&#39;esecuzione precedente, eseguire il comando seguente in CLI (solo architettura Pro): `zgrep "\" 50[0-9]" /path/to/access.log.<rotation ID>.gz`
1. Controllare quindi `exception.log` e `error.log` o il [registro ruotato](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/configuration.html?lang=it#log-rotation) equivalente (registri che vengono ruotati e compressi automaticamente quando raggiungono una determinata dimensione del file) per la stessa marca temporale per individuare il potenziale errore e vedere cosa potrebbe essersi verificato per causarlo. Nota: per controllare `exception.log` e `error.log`, eseguire i comandi indicati sopra nell&#39;interfaccia CLI ma sostituire `access.log` con `exception.log` o `error.log`.

## Lettura correlata

* Consulta [Visualizzare e gestire i registri](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html?lang=it) nella *Guida di Adobe Commerce sull&#39;infrastruttura cloud*.
* Consulta [Risoluzione dei problemi relativi agli errori 503](/help/troubleshooting/miscellaneous/troubleshooting-503-errors.md) nella Knowledge Base di supporto.