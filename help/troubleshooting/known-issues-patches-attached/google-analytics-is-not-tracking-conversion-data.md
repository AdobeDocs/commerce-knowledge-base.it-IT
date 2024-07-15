---
title: Google Analytics non tiene traccia dei dati di conversione
description: Questo articolo fornisce una patch per il problema noto di Adobe Commerce 2.2.4 relativo alle Google Analytics che non tengono traccia dei dati di conversione.
exl-id: b9012fd1-4f90-41e9-9559-0343ee052ec6
feature: Configuration, Observability
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---

# Google Analytics non tiene traccia dei dati di conversione

Questo articolo fornisce una patch per il problema noto di Adobe Commerce 2.2.4 relativo alle Google Analytics che non tengono traccia dei dati di conversione.

>[!NOTE]
>
>Il problema è stato risolto in Adobe Commerce 2.2.6.

## Problema

I dati di conversione non sono stati tracciati dalle Google Analytics a causa di un errore nel codice del componente Google Analytics.

<u>Passaggi da riprodurre</u>:

1. Abilita e configura la funzionalità Google Analytics nell&#39;amministratore di Commerce in **Archivi** > **Impostazioni** > **Configurazione** > **Vendite** > **API Google** > **Google Analytics**.
1. Fai clic su **Salva configurazione**.
1. Effettua un ordine sul vetrina.
1. Vai a **Dashboard Google Analytics** > **Conversioni** > **Panoramica**.
1. Imposta l’intervallo di date sulla data corrente.

<u>Risultato previsto</u>:

L’ordine viene visualizzato nei dati di conversione.

<u>Risultato effettivo</u>:

L’ordine non viene visualizzato nei dati di conversione.

## Soluzione

La patch corregge l’errore nel codice del componente Google Analytics. Dopo l’applicazione della patch, i dati di conversione vengono tracciati dalle Google Analytics.

## Patch

La patch è allegata a questo articolo. Per scaricarlo, scorri verso il basso fino alla fine dell’articolo e fai clic sul nome del file o sul seguente collegamento:

[Scarica MDVA-11263\_EE\_2.2.4\_v1.compositore.patch](assets/MDVA-11263_EE_2.2.4_v1.composer.patch.zip)

### Versioni compatibili di Adobe Commerce:

La patch è stata creata per:

* Adobe Commerce on-premise 2.2.4

La patch è compatibile (ma potrebbe non risolvere il problema) anche con le seguenti versioni ed edizioni di Adobe Commerce:

* Adobe Commerce on-premise 2.2.5
* Adobe Commerce sull’infrastruttura cloud 2.2.4, 2.2.5

## Come applicare il cerotto

Per istruzioni, vedere [Come applicare una patch del compositore fornita da Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md).

## File allegati
