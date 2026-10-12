---
title: Consultate i registri per risolvere i problemi relativi agli errori 500 e 503 in Adobe Commerce
description: Questo articolo spiega come controllare il "access.log" e i relativi registri per risolvere i problemi relativi agli errori 503 e 500, che possono essere causati da traffico o risorse server insufficienti. La visualizzazione di "access.log" e dei relativi registri può fornire informazioni su ciò che potrebbe causare problemi relativi ad Adobe Commerce sull’infrastruttura cloud.
exl-id: 47d7de6b-3e12-4e79-a5c1-c27a9196b99c
feature: Cloud, Logs
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: 3c398179-d35a-51ba-b317-6c5b95feef5e
    internal-label: Logs
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%
---
# Consultate i registri per risolvere i problemi relativi agli errori 500 e 503 in Adobe Commerce

In questo articolo viene illustrato come controllare `access.log` e i registri correlati per risolvere gli errori 503 e 500, che possono essere causati da traffico o risorse server insufficienti. La visualizzazione di `access.log` e dei relativi registri può fornire informazioni su ciò che potrebbe causare problemi relativi ad Adobe Commerce sull&#39;infrastruttura cloud.

<!--
Bob - not in TOC
-->

## Prodotti e versioni interessati

* Adobe Commerce sull&#39;infrastruttura cloud, tutte le [versioni supportate](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/lifecycle-policy.html).

Per visualizzare i registri per questi errori del server, controllare `access.log` sul server Web, ad esempio `<ip address>` `<timestamp>` `<request uri>` `<response code>` `<referer url>`

Per controllare i registri correlati:

1. Esegui il seguente comando nella CLI se si trova nel giorno corrente (per Adobe Commerce su infrastruttura cloud, architettura del piano Pro). Oppure fino a un certo punto nel passato (per Adobe Commerce sull&#39;infrastruttura cloud Architettura del piano Starter), poiché la durata della copertura dei registri è limitata e la rotazione dei registri non è disponibile: `grep -r "\" [50[0-9]" /path/to/access.log` Se l&#39;errore si è verificato nell&#39;esecuzione precedente, eseguire il comando seguente in CLI (solo architettura Pro): `zgrep "\" 50[0-9]" /path/to/access.log.<rotation ID>.gz`
1. Controllare quindi `exception.log` e `error.log` o il [registro ruotato](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/configuration.html#log-rotation) equivalente (registri che vengono ruotati e compressi automaticamente quando raggiungono una determinata dimensione del file) per la stessa marca temporale per individuare il potenziale errore e vedere cosa potrebbe essersi verificato per causarlo. Nota: per controllare `exception.log` e `error.log`, eseguire i comandi indicati sopra nell&#39;interfaccia CLI ma sostituire `access.log` con `exception.log` o `error.log`.

## Lettura correlata

* Consulta [Visualizzare e gestire i registri](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html) nella *Guida di Adobe Commerce sull&#39;infrastruttura cloud*.
* Consulta [Risoluzione dei problemi relativi agli errori 503](/help/troubleshooting/miscellaneous/troubleshooting-503-errors.md) nella Knowledge Base di supporto.