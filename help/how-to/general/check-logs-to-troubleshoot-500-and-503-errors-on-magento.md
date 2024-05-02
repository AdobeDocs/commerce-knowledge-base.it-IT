---
title: Consultate i registri per risolvere i problemi relativi agli errori 500 e 503 in Adobe Commerce
description: Questo articolo spiega come controllare il "access.log" e i relativi registri per risolvere i problemi relativi agli errori 503 e 500, che possono essere causati da traffico o risorse server insufficienti. La visualizzazione di "access.log" e dei relativi registri può fornire informazioni su ciò che potrebbe causare problemi relativi ad Adobe Commerce sull’infrastruttura cloud.
exl-id: 47d7de6b-3e12-4e79-a5c1-c27a9196b99c
feature: Cloud, Logs
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---

# Consultate i registri per risolvere i problemi relativi agli errori 500 e 503 in Adobe Commerce

Questo articolo spiega come controllare `access.log` e i relativi registri per la risoluzione dei problemi relativi agli errori 503 e 500, che possono essere causati da traffico o risorse server insufficienti. Visualizzazione di `access.log` e i relativi registri possono fornire informazioni su ciò che potrebbe causare problemi relativi ad Adobe Commerce sull’infrastruttura cloud.

<!--
Bob - not in TOC
-->

## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud, tutto [versioni supportate](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/lifecycle-policy.html).

Per visualizzare i registri relativi a questi errori del server, controllare `access.log` sul server web, ad esempio `<ip address>` `<timestamp>` `<request uri>` `<response code>` `<referer url>`

Per controllare i registri correlati:

1. Esegui il seguente comando nella CLI se si trova nel giorno corrente (per Adobe Commerce su infrastruttura cloud, architettura del piano Pro). O fino a un certo punto nel passato (per Adobe Commerce sull’architettura del piano Starter per l’infrastruttura cloud), poiché la durata della copertura dei registri è limitata e la rotazione dei registri non è disponibile: `grep -r "\" [50[0-9]" /path/to/access.log` Se l&#39;errore si è verificato in precedenza, eseguire il comando seguente in CLI (solo architettura Pro): `zgrep "\" 50[0-9]" /path/to/access.log.<rotation ID>.gz`
1. Quindi seleziona la `exception.log` e `error.log` o l&#39;equivalente [registro ruotato](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/configuration.html#log-rotation) (registri che vengono ruotati e compressi automaticamente quando raggiungono una determinata dimensione del file) per la stessa marca temporale per individuare il potenziale errore e vedere cosa potrebbe essersi verificato per causarlo. Nota: per controllare `exception.log` e `error.log` esegui i comandi di cui sopra nella CLI ma sostituisci `access.log` con `exception.log` o `error.log`.

## Lettura correlata

* Consulta [Visualizzare e gestire i registri](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html) nel *Guida di Adobe Commerce sull’infrastruttura cloud*.
* Consulta [Risoluzione dei problemi relativi agli errori 503](/help/troubleshooting/miscellaneous/troubleshooting-503-errors.md) nella nostra knowledge base di supporto.
* Consulta [Risoluzione dei problemi relativi al sito Magento inattivo](/help/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.md) nella nostra knowledge base di supporto.
