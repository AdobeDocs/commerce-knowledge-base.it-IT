---
title: Errori di distribuzione in cui non sono state trovate patch
description: "Questo articolo fornisce una soluzione al problema relativo a un errore *Le patch successive non sono state trovate: MDVA-XXXXX, ACSD-XXXXX. Verificare con il comando 'status' la disponibilità di queste patch per la versione corrente del Magento*."
exl-id: 5a2fd35a-892a-48af-a41f-f275297b3e2e
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Errori di distribuzione in cui non sono state trovate patch

Questo articolo fornisce una soluzione al problema che si verifica quando si aggiorna l&#39;istanza la distribuzione non riesce e viene visualizzato un errore nei registri di distribuzione: *Impossibile trovare le patch successive: MDVA-XXXXX, ACSD-XXXXX. Verificare la disponibilità del comando &quot;status&quot; di queste patch per la versione di Magento corrente*.

## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud, [tutte le versioni supportate](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).


## Problema

Si è verificato un errore durante l&#39;aggiornamento di Adobe Commerce: *Impossibile trovare le patch successive*.

## Causa

Le patch applicate in precedenza per le versioni precedenti non sono applicabili o non sono più disponibili per la nuova versione.

## Soluzione

1. Controlla il file `.magento.env.yaml` nella sezione QUALITY_PATCH, ad esempio

   ```yaml
   QUALITY_PATCHES:
    - MDVA-XXXXX
    - ACSD-XXXXX
   ```

1. Cerca gli ID patch nelle [Note sulla versione delle patch di qualità](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html) per verificare se è possibile applicarli alla nuova versione di Adobe Commerce a cui stai eseguendo l&#39;aggiornamento.
1. Se la patch non è applicabile alla nuova versione di Adobe Commerce in cui si desidera eseguire l&#39;aggiornamento, rimuovere l&#39;ID patch dal file `.magento.env.yaml`.
1. Dopo aver rivisto tutti gli ID patch indicati dall’errore, invia le modifiche e ridistribuiscili.

## Lettura correlata

* [Applicare le patch](/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=en#apply-a-patch-in-a-local-environment) nella Guida all&#39;infrastruttura di Commerce su Cloud.
