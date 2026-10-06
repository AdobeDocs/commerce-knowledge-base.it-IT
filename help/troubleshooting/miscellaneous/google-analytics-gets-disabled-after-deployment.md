---
title: Google Analytics viene disabilitato dopo la distribuzione
description: In questo argomento viene illustrata la soluzione di un problema tipico che potrebbe verificarsi con Google Analytics durante la distribuzione.
exl-id: ecf6a277-2dfa-45cf-b86f-9a27f39017f4
feature: Build, Deploy, Variables
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%
---
# Google Analytics viene disabilitato dopo la distribuzione

In questo argomento viene illustrata la soluzione di un problema tipico che potrebbe verificarsi con Google Analytics durante la distribuzione.

## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud, tutte le versioni

## Problema

Quando si distribuisce il codice in ambienti diversi, gli script di compilazione e distribuzione verificano che il ramo `master/production/staging` sia distribuito per mantenere abilitato Google Analytics. Durante la distribuzione di rami di sviluppo (o secondari) di master in ambienti di sviluppo (integrazione), lo script di distribuzione disabilita Google Analytics.

## Causa

Questa è una funzione progettata per garantire che i dati e le interazioni degli sviluppatori non vengano inviati a Google Analytics o tracciati da.

## Soluzione

Se si desidera che Google Analytics sia sempre abilitato, impostare la variabile di distribuzione `ENABLE_GOOGLE_ANALYTICS = true`, come descritto in [Distribuire variabili](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#enable_google_analytics) nella documentazione per gli sviluppatori.

>[!NOTE]
>
>Siamo consapevoli che questo articolo può ancora contenere termini software standard del settore che alcuni possono trovare razzisti, sessisti o oppressivi e che possono far sentire il lettore ferito, traumatizzato, o sgradito. Adobe sta lavorando per rimuovere questi termini dal nostro codice, dalla nostra documentazione e dalle esperienze utente.
