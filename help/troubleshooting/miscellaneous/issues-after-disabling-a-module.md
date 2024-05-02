---
title: Problemi dopo la disattivazione di un modulo
description: Questo articolo fornisce una soluzione per i problemi di funzionalità dei moduli dopo aver disabilitato l’output dei moduli in Commerce Admin.
exl-id: 517f6993-f09e-4a94-8c57-175ecf9a98a8
feature: Extensions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 0%

---

# Problemi dopo la disattivazione di un modulo

Questo articolo fornisce una soluzione per i problemi di funzionalità dei moduli dopo aver disabilitato l’output dei moduli in Commerce Admin.

## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud 2.1.X o versione precedente
* Adobe Commerce on-premise 2.1.X o precedente

## Problema

Dopo aver disabilitato l’output del modulo in Commerce Admin, in **Negozi** > **Impostazioni** > **Configurazione** > AVANZATE > **Avanzate**, è possibile che si verifichino problemi relativi alla funzionalità del modulo.

## Causa

Disabilitazione dell’output di un modulo in **Negozi** > **Impostazioni** > **Configurazione** > AVANZATE > **Avanzate** disabilita solo l’output (HTML, JS), ma non disabilita la funzionalità di questo modulo.

## Soluzione

Se devi disattivare la funzionalità del modulo, disattiva il modulo come descritto in [Abilitare o disabilitare i moduli](https://devdocs.magento.com/guides/v2.1/install-gde/install/cli/install-cli-subcommands-enable.html) nella documentazione per gli sviluppatori.

La funzionalità di disabilitazione dell’output del modulo è stata rimossa a partire dalla versione 2.2.0.
