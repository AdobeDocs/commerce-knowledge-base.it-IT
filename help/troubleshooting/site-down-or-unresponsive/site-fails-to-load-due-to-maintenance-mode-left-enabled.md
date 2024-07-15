---
title: Impossibile caricare il sito a causa della modalità di manutenzione rimasta abilitata
description: "Questo articolo corregge il mancato caricamento del sito a causa della mancata attivazione o disattivazione automatica della modalità di manutenzione. Potresti ricevere un messaggio di errore: *Servizio temporaneamente non disponibile Il server non è al momento in grado di soddisfare la richiesta a causa di tempi di inattività della manutenzione o problemi di capacità.*"
exl-id: 77e01588-e135-4d24-a0c4-1a6ee123f4a8
feature: Support
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Impossibile caricare il sito a causa della modalità di manutenzione rimasta abilitata

Questo articolo corregge i casi in cui il sito non viene caricato a causa di una modalità di manutenzione che viene lasciata attivata o non disabilitata automaticamente. È possibile che venga visualizzato un messaggio di errore: *Servizio temporaneamente non disponibile Il server non è al momento in grado di soddisfare la richiesta a causa di tempi di inattività di manutenzione o problemi di capacità.*

## Versioni e prodotti interessati

* Adobe Commerce sull’infrastruttura cloud 2.2.x, 2.3.x
* Adobe Commerce on-premise 2.2.x, 2.3.x

## Problema

La modalità di manutenzione fa parte del processo di distribuzione. Tuttavia, se è stata abilitata automaticamente e non è stata disabilitata oppure se la modalità di manutenzione del commerciante è stata abilitata manualmente e si è dimenticata di disabilitare, potrebbe verificarsi un errore di distribuzione.

## Causa

L’attivazione della modalità di manutenzione impedisce il caricamento del sito.

## Soluzione

Per verificare lo stato della modalità di manutenzione corrente, eseguire il comando seguente da CLI:

```
bin/magento maintenance:status
```

Per disattivare la modalità di manutenzione, eseguire il comando seguente in CLI:

```
bin/magento maintenance:disable
```

## Lettura correlata

Per informazioni su quando utilizzare la modalità di manutenzione, consultare [Attiva o disattiva la modalità di manutenzione](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=maintenance%20mode) nella documentazione per gli sviluppatori.
