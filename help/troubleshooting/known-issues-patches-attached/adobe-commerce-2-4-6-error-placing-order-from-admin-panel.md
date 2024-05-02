---
title: Errore Adobe Commerce 2.4.6 nell’effettuare l’ordine dal pannello di amministrazione
description: Questo articolo fornisce una patch per il problema noto di Adobe Commerce on cloud infrastructure 2.4.6 che si blocca sulla selezione del negozio dopo aver effettuato un ordine dal pannello di amministrazione di Commerce.
feature: Admin Workspace
role: Developer
exl-id: b30be5a5-3681-41db-9040-3624faed7c46
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# Errore Adobe Commerce 2.4.6 nell’effettuare l’ordine dal pannello di amministrazione

Questo articolo fornisce una patch per il problema noto di Adobe Commerce on cloud infrastructure 2.4.6 che si blocca sulla selezione del negozio dopo aver effettuato un ordine dal pannello di amministrazione di Commerce.

## Problema

Quando effettui un ordine dal pannello di amministrazione, la selezione dei punti vendita è bloccata.

<u>Passaggi da riprodurre</u>

1. Vai a **[!UICONTROL Sales]** > **[!UICONTROL Orders]** e selezionare un cliente per creare un ordine.
2. Selezionare il punto vendita per effettuare l&#39;ordine dalla schermata del selettore del punto vendita.

<u>Risultato previsto</u>

Dopo aver selezionato il negozio, si è in grado di completare l&#39;ordine.

<u>Risultato effettivo:</u>

Dopo aver selezionato il negozio, vieni reindirizzato alla pagina del selettore del negozio e non puoi creare un ordine.

## Patch

Fai clic sul seguente collegamento per scaricare la patch.

[Scarica ACSD-52277_2.4.6.patch](assets/ACSD-52277_2.4.6.patch.zip)

### Versioni compatibili di Adobe Commerce

La patch è stata creata per e compatibile con Adobe Commerce on cloud infrastructure e Adobe Commerce on-premise 2.4.6 e 2.4.6-p1.

## Come applicare il cerotto

* Per istruzioni sull’applicazione di patch per Adobe Commerce sull’infrastruttura cloud, consulta [Applicare le patch](/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella Guida all’infrastruttura Commerce on Cloud.
* Per istruzioni sull’applicazione di patch per Adobe Commerce on-premise, fare riferimento a [Applicare le patch](/docs/commerce-operations/upgrade-guide/patches/apply.html?lang=en#composer) nella Guida all’aggiornamento di Commerce.
