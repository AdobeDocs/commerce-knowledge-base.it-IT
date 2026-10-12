---
title: Sito in modalità manutenzione, ma disponibile per i clienti
description: Questo articolo fornisce una correzione per quando è abilitata la modalità di manutenzione (un problema di Adobe Commerce sull’infrastruttura cloud), ma la vetrina è ancora disponibile per i clienti.
exl-id: 61b81fbd-a382-44b5-94e9-5b6d72f11349
feature: Cache
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '159'
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
