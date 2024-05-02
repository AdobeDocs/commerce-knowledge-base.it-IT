---
title: Moduli mancanti in Adobe Commerce 2.4.4
description: Questo articolo fornisce una soluzione al problema che si verifica quando i moduli inclusi nelle versioni precedenti di Adobe Commerce non sono presenti nella versione 2.4.4.
exl-id: c0335b66-803b-44d7-b966-7d60a5f21d8d
feature: Extensions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---

# Moduli mancanti in Adobe Commerce 2.4.4

Questo articolo fornisce una soluzione per i casi in cui i moduli inclusi nelle versioni precedenti di Adobe Commerce non sono presenti nella versione 2.4.4.

## Prodotti e versioni interessati

* Adobe Commerce (tutti i metodi di distribuzione) tutto  [versioni supportate](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problema

Non puoi installare un modulo di terze parti o hai rilevato che alcune delle estensioni core in bundle non sono presenti quando hai effettuato l’aggiornamento ad Adobe Commerce 2.4.4. Questo dovrebbe derivare solo dall’installazione di un modulo di terze parti che richiede una delle estensioni in bundle rimosse da Adobe Commerce 2.4.4 o se il progetto utilizza alcune delle funzionalità di uno dei moduli rimossi.

* Scenario 1: il progetto ha utilizzato una delle funzionalità principali del modulo in bundle. Il modulo in bundle utilizzato non è incluso in Adobe Commerce 2.4.4. Dopo l’aggiornamento a Adobe Commerce 2.4.4, ti rendi conto che il modulo e la relativa funzionalità non sono presenti.

* Scenario 2: nel progetto corrente è installato un modulo con una dipendenza da uno dei moduli in bundle rimossi.

Questo comportamento è previsto in quanto le estensioni in bundle con il fornitore sono state rimosse dalla base di codice di Adobe Commerce 2.4.4.

## Soluzione

Installa/acquista separatamente le estensioni ufficiali. Questi sono disponibili sul sito [Commerce Marketplace](https://marketplace.magento.com/extensions.html).

## Lettura correlata

[Estensioni in bundle con il fornitore](https://experienceleague.adobe.com/docs/commerce-operations/release/notes/adobe-commerce/2-4-4.html?#vendor-bundled-extensions) in Documentazione di Adobe Commerce > Informazioni sulla versione > Note sulla versione di Adobe Commerce 2.4.4.
