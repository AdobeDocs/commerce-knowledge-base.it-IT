---
title: Sito in modalità manutenzione, ma disponibile per i clienti
description: Questo articolo fornisce una correzione per quando è abilitata la modalità di manutenzione (un problema di Adobe Commerce sull’infrastruttura cloud), ma la vetrina è ancora disponibile per i clienti.
exl-id: 61b81fbd-a382-44b5-94e9-5b6d72f11349
feature: Cache
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 0%

---

# Sito in modalità manutenzione, ma disponibile per i clienti

Questo articolo fornisce una correzione per quando è abilitata la modalità di manutenzione (un problema di Adobe Commerce sull’infrastruttura cloud), ma la vetrina è ancora disponibile per i clienti.

## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud (tutte le versioni)

## Problema

<u>Passaggi da riprodurre:</u>

1. Attiva la modalità di manutenzione per il sito.
1. Passa alla vetrina.

<u>Risultato previsto:</u>

Viene visualizzata la pagina di manutenzione.

<u>Risultato effettivo:</u>

Le pagine di vetrina vengono visualizzate come di consueto.

## Causa

Le pagine vengono ancora memorizzate nella cache, pertanto la pagina di manutenzione non viene visualizzata.

## Soluzione visibile al sito nonostante sia in modalità di manutenzione

1. SSH per l’ambiente.
1. Eseguire il comando `php bin/magento cache:clean`.

## Lettura correlata

[Attiva o disattiva la modalità di manutenzione](https://experienceleague.adobe.com/it/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) nella documentazione per gli sviluppatori.
