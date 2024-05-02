---
title: E-mail ordine inviata dall’indirizzo e-mail del server
description: Questo articolo fornisce una patch per il problema noto di Adobe Commerce on cloud infrastructure 2.2.4 relativo all’invio di e-mail di ordine dall’indirizzo e-mail del server.
exl-id: f32e0c09-e19e-4269-bbba-0533d74a7f49
feature: Communications
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# E-mail ordine inviata dall’indirizzo e-mail del server

Questo articolo fornisce una patch per il problema noto di Adobe Commerce on cloud infrastructure 2.2.4 relativo all’invio di e-mail di ordine dall’indirizzo e-mail del server.

## Problema

Le e-mail di conferma dell’ordine vengono inviate dall’indirizzo e-mail del server Apache. Altre e-mail (password dimenticata e così via) vengono inviate dagli indirizzi e-mail configurati.

<u>Passaggi da riprodurre</u>:

1. Effettua un ordine con **Invia conferma ordine** casella selezionata.
1. Controlla l’e-mail.

<u>Risultato previsto</u>:

L’e-mail è stata inviata dall’indirizzo di invio configurato da Adobe Commerce.

<u>Risultato effettivo</u>:

L’e-mail è stata inviata dall’indirizzo e-mail configurato nel server Apache in uso.

## Patch

La patch è allegata a questo articolo. Per scaricarlo, scorri verso il basso fino alla fine dell’articolo e fai clic sul nome del file, oppure fai clic sul seguente collegamento:

[Scarica MDVA-10993\_EE\_2.2.4\_v1.compositore.patch](assets/MDVA-10993_EE_2.2.4_v1.composer.patch.zip)

### Versioni compatibili di Adobe Commerce:

La patch è stata creata per:

* Adobe Commerce sull’infrastruttura cloud 2.2.4

La patch è compatibile (ma potrebbe non risolvere il problema) anche con le seguenti versioni ed edizioni di Adobe Commerce:

* Adobe Commerce sull’infrastruttura cloud 2.2.5
* Adobe Commerce sull’infrastruttura cloud 2.2.6
* Adobe Commerce sull’infrastruttura cloud 2.2.7
* Adobe Commerce sull’infrastruttura cloud 2.2.8
* Adobe Commerce on-premise 2.2.4
* Adobe Commerce on-premise 2.2.5
* Adobe Commerce on-premise 2.2.6
* Adobe Commerce on-premise 2.2.7
* Adobe Commerce on-premise 2.2.8
* Adobe Commerce on-premise 2.3.0

## Come applicare il cerotto

Per istruzioni, consulta [Come applicare una patch del compositore fornita dall&#39;Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) nella nostra knowledge base di supporto.

## File allegati
