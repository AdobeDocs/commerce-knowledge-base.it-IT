---
title: Impossibile convalidare il numero di partita IVA - Adobe Commerce sull’infrastruttura cloud
description: Questo articolo fornisce una patch per il problema in cui si verifica un errore durante la verifica del numero di partita IVA.
exl-id: 9868e888-bad8-4823-acab-4b3804933cb0
feature: Cloud, Customer Service, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# Impossibile convalidare il numero di partita IVA - Adobe Commerce sull’infrastruttura cloud

Questo articolo fornisce una patch per il problema in cui si verifica un errore durante la verifica del numero di partita IVA.

## Prodotti e versioni interessati

Sono state interessate tutte le versioni di Adobe Commerce on-premise e Adobe Commerce on cloud infrastructure fino alla versione 2.3.6 (inclusa la versione 2.3.5-p1), incluse quelle già rilasciate per le versioni p1 e p2. Ciò include:

* 2.3.5-p1
* 2.3.5.
* 2.3.4 - 2.3.4-p2
* 2,3,3 - 2,3,3-p1
* 2,3,2-2,3,2-p2
* 2,0,0 - 2,3,1

## Problema

<u>Passaggi da riprodurre:</u>

1. Vai a **Negozi** > **Configurazione** > **Clienti** > **Configurazione cliente** > **Crea nuove opzioni account** e imposta **Abilita assegnazione automatica** a **Gruppo di clienti** a *Sì*.
1. Vai a **Generale** > **Informazioni sul negozio** > e imposta un paese e un numero di partita IVA validi.
1. Fai clic su **Convalida partita IVA**.

<u>Risultato previsto:</u>

Convalida completata.

<u>Risultato effettivo:</u>

Viene visualizzato il seguente errore: &quot;*Errore durante la verifica della partita IVA.*&quot;

## Soluzione

Applica [patch](assets/MDVA-27623_EE_2.3.2-p2_COMPOSER_v1.patch.zip) fornite nel presente articolo.

## Patch

La patch è allegata a questo articolo. Per scaricarlo, scorri verso il basso fino alla fine dell’articolo e fai clic sul nome del file, oppure fai clic sul seguente collegamento:

[MDVA-27623\_EE\_2.3.2-p2\_COMPOSER\_v1.patch](assets/MDVA-27623_EE_2.3.2-p2_COMPOSER_v1.patch.zip)

## Come applicare il cerotto

Consulta [Come applicare una patch del compositore fornita dall&#39;Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) per istruzioni.

## File allegati
