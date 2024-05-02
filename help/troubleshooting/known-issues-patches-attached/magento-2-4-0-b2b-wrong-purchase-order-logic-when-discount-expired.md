---
title: "Adobe Commerce 2.4.0 B2B: logica dell’ordine di acquisto errata alla scadenza dello sconto"
description: Questo articolo fornisce una patch per l’emissione nota di uno sconto su ordine di acquisto (OA) non applicato in Adobe Commerce 2.4.0 B2B. Se l'ordine di acquisto è stato inserito con un codice sconto scaduto mentre l'ordine di acquisto era in fase di approvazione, l'ordine approvato non riflette lo sconto.
exl-id: 3ef41655-c31e-4e9c-8985-fa1b4fd53170
feature: B2B, Orders, Payments, Personalization, Purchase Orders
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 B2B: logica dell’ordine di acquisto errata alla scadenza dello sconto

Questo articolo fornisce una patch per l’emissione nota di uno sconto su ordine di acquisto (OA) non applicato in Adobe Commerce 2.4.0 B2B. Se l&#39;ordine di acquisto è stato inserito con un codice sconto scaduto mentre l&#39;ordine di acquisto era in fase di approvazione, l&#39;ordine approvato non riflette lo sconto.

## Prodotti e versioni interessati

* Adobe Commerce sull’infrastruttura cloud 2.4.0
* Adobe Commerce on-premise 2.4.0

## Problema

<u>Prerequisiti</u>: viene creato un coupon di sconto e esistono regole di approvazione che impediscono l’elaborazione automatica degli OA.

<u>Passaggi da riprodurre:</u>

1. Inserire un ordine di acquisto con uno sconto applicato.
1. Disattiva il buono sconto.
1. Approva OA come responsabile.
1. Controlla l’ordine creato come risultato.

<u>Risultato previsto:</u>

L&#39;ordine viene creato con un totale scontato.

<u>Risultato effettivo:</u>

L&#39;ordine viene creato per l&#39;intero importo.

## Soluzione

Applichi la patch fornita in questo articolo.

## Patch

La patch è allegata a questo articolo. Per scaricarlo, scorri verso il basso fino alla fine dell’articolo e fai clic sul nome del file, oppure fai clic sul seguente collegamento:

[B2B-709-composer.patch](assets/B2B-709-composer.patch.zip)

La patch è disponibile anche per il download in entrambi, `.git` e `.composer` , formati su [Download di Adobe Commerce](https://magento.com/tech-resources/download) pagina, sotto **Patch** nella navigazione a sinistra della colonna. Cercare la patch XXX.

## Come applicare il cerotto

Consulta [Come applicare una patch del compositore fornita dall&#39;Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) nella knowledge base di supporto per le istruzioni.
