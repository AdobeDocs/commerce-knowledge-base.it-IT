---
title: Patch non trovata durante la distribuzione o l'applicazione manuale
description: 'Questo articolo fornisce una soluzione al problema relativo a un errore *Le patch successive non sono state trovate: MDVA-XXXXX, ACSD-XXXXX. Verificare la disponibilità di queste patch per la versione corrente di Magento utilizzando il comando ''stato''*.'
exl-id: 5a2fd35a-892a-48af-a41f-f275297b3e2e
source-git-commit: 180f0e00ec1a2c6c3bd2ebca4dafe387c7bb3852
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# Patch non trovata durante la distribuzione o l&#39;applicazione manuale

Questo articolo fornisce una soluzione al problema che si verifica quando si aggiorna l&#39;istanza la distribuzione non riesce e viene visualizzato un errore nei registri di distribuzione: *Impossibile trovare le patch successive: MDVA-XXXXX, ACSD-XXXXX. Verificare la disponibilità di queste patch per la versione corrente di Magento utilizzando il comando &quot;status&quot;*.

## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud, [tutte le versioni supportate](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problema

Si è verificato un errore durante l&#39;aggiornamento di Adobe Commerce: *Impossibile trovare le patch successive*.

## Causa

Le patch applicate in precedenza per le versioni precedenti non sono applicabili o non sono più disponibili per la nuova versione.

Questo problema può verificarsi anche quando il pacchetto dello strumento Patch di qualità installato (`magento/quality-patches`) è obsoleto.

Ad esempio:

Caso 1:
* Un cerotto potrebbe essere stato originariamente disponibile per 2.4.7-p9 nel QPT 1.1.71
* Una versione più recente di QPT (ad esempio, 1.1.72) potrebbe aggiungere in seguito il supporto per 2.4.7-p10
* Se il cliente aggiorna Commerce alla versione 2.4.7-p10 ma mantiene installata una versione precedente di QPT, QPT potrebbe non riconoscere che esiste una variante di patch compatibile per la versione 2.4.7-p10

Caso 2:
* È possibile che sia stata aggiunta una patch in QPT 1.1.72
* Se il cliente mantiene installata una versione precedente di QPT, QPT non riconoscerà l’esistenza della patch

In questi casi, l’applicazione della patch può non riuscire e viene visualizzato un messaggio di questo tipo:

```
Next patches weren't found: ACSD-12345.
Check the availability of these patches for the  current Magento version using the "status" command.
```

Ciò si verifica perché la versione QPT installata non è in grado di mappare la versione corrente di Commerce a una versione applicabile della patch.

## Soluzione

Questo problema non è limitato alle distribuzioni che applicano patch tramite `.magento.env.yaml`. Lo stesso problema di base può verificarsi anche quando si applica manualmente una patch con:

```bash
vendor/bin/magento-patches apply <PATCH_ID>
```

Ad esempio:

```
Next patches weren't found: ACSD-12345
Check the availability of these patches for the  current Magento version using the "status" command.
```

In questo caso, la patch non è disponibile per la versione di Adobe Commerce installata nell’ambiente in cui viene eseguito il comando.

1. Controlla il file `.magento.env.yaml` nella sezione QUALITY_PATCHES, ad esempio

   ```yaml
   QUALITY_PATCHES:
    * MDVA-XXXXX
    * ACSD-XXXXX
   ```

1. Cerca gli ID patch nelle [Note sulla versione delle patch di qualità](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/release-notes.html) per verificare se è possibile applicarli alla nuova versione di Adobe Commerce a cui stai eseguendo l&#39;aggiornamento.
1. Se la patch non è applicabile alla nuova versione di Adobe Commerce in cui si desidera eseguire l&#39;aggiornamento, rimuovere l&#39;ID patch dal file `.magento.env.yaml`.
1. Dopo aver rivisto tutti gli ID patch indicati dall’errore, invia le modifiche e ridistribuiscili.

## Lettura correlata

* [Applicare le patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=en#apply-a-patch-in-a-local-environment) nella Guida all&#39;infrastruttura di Commerce su Cloud.
