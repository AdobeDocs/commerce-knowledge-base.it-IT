---
title: Problemi dopo la disattivazione di un modulo
description: Questo articolo fornisce una soluzione per i problemi di funzionalità dei moduli dopo aver disabilitato l’output dei moduli in Commerce Admin.
exl-id: 517f6993-f09e-4a94-8c57-175ecf9a98a8
feature: Extensions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

Dopo aver disabilitato l&#39;output del modulo nell&#39;amministrazione di Commerce, in **Archivi** > **Impostazioni** > **Configurazione** > AVANZATE > **Avanzate**, è possibile che si verifichino problemi relativi alla funzionalità del modulo.

## Causa

Se si disabilita l&#39;output di un modulo in **Archivi** > **Impostazioni** > **Configurazione** > AVANZATE > **Avanzate**, verrà disabilitato solo l&#39;output (HTML, JS), ma non la funzionalità del modulo.

## Soluzione

Se devi disabilitare la funzionalità del modulo, disabilita il modulo come descritto in [Abilita o disabilita i moduli](https://experienceleague.adobe.com/it/docs/commerce-operations/installation-guide/tutorials/manage-modules) nella documentazione per gli sviluppatori.

La funzionalità di disabilitazione dell’output del modulo è stata rimossa a partire dalla versione 2.2.0.
