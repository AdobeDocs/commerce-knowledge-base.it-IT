---
title: La Google Analytics viene disabilitata dopo la distribuzione
description: In questo argomento viene illustrata la soluzione di un problema tipico che può verificarsi con le Google Analytics durante la distribuzione.
exl-id: ecf6a277-2dfa-45cf-b86f-9a27f39017f4
feature: Build, Deploy, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---

# La Google Analytics viene disabilitata dopo la distribuzione

In questo argomento viene illustrata la soluzione di un problema tipico che può verificarsi con le Google Analytics durante la distribuzione.

## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud, tutte le versioni

## Problema

Durante la distribuzione del codice tra ambienti, gli script di compilazione e distribuzione verificano che il ramo `master/production/staging` sia distribuito per mantenere abilitate le Google Analytics. Quando si distribuiscono rami di sviluppo (o secondari) di master in ambienti di sviluppo (integrazione), lo script di distribuzione disabilita le Google Analytics.

## Causa

Questa è una funzione progettata per garantire che i dati e le interazioni degli sviluppatori non vengano inviati o tracciati dalle Google Analytics.

## Soluzione

Se si desidera che le Google Analytics siano sempre abilitate, impostare la variabile di distribuzione `ENABLE_GOOGLE_ANALYTICS = true`, come descritto in [Distribuire variabili](https://devdocs.magento.com/guides/v2.3/cloud/env/variables-deploy.html#enable_google_analytics) nella documentazione per gli sviluppatori.

>[!NOTE]
>
>Siamo consapevoli che questo articolo può ancora contenere termini software standard del settore che alcuni possono trovare razzisti, sessisti o oppressivi e che possono far sentire il lettore ferito, traumatizzato, o sgradito. Adobe sta lavorando per rimuovere questi termini dal nostro codice, dalla nostra documentazione e dalle esperienze utente.
