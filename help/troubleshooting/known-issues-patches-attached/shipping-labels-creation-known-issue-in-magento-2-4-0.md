---
title: Problema noto nella creazione di etichette di spedizione in Adobe Commerce 2.4.0
description: Questo articolo fornisce una patch per un problema noto di Adobe Commerce 2.4.0, in cui non è possibile creare un’etichetta di spedizione.
exl-id: 722689d9-0c90-4a9d-8449-e93c6585b7c3
feature: Orders, Shipping/Delivery
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# Problema noto nella creazione di etichette di spedizione in Adobe Commerce 2.4.0

Questo articolo fornisce una patch per un problema noto di Adobe Commerce 2.4.0, in cui non è possibile creare un’etichetta di spedizione.

## Prodotti e versioni interessati

* Adobe Commerce on-premise 2.4.0
* Adobe Commerce sull’infrastruttura cloud 2.4.0

## Problema

<u>Prerequisiti</u>: crea un ordine utilizzando il metodo di spedizione FedEx, DHL, UPS o USPS.

### Scenario 1: creare un&#39;etichetta quando si aggiunge una spedizione

<u>Passaggi da riprodurre:</u>

1. Apri l&#39;ordine effettuato nell&#39;amministratore in **Vendite** > **Ordini**.
1. Fare clic sul pulsante **Spedisci**. Viene visualizzata la pagina **Nuova spedizione**.

<u>Risultato previsto:</u>

Nella parte inferiore della pagina viene visualizzata la casella di controllo **Crea etichetta di spedizione**.

<u>Risultato effettivo:</u>

La casella di controllo **Crea etichetta di spedizione** non è visualizzata.

### Scenario 2: creare un&#39;etichetta per la spedizione esistente

<u>Passaggi da riprodurre:</u>

1. Apri l&#39;ordine effettuato nell&#39;amministratore in **Vendite** > **Ordini**.
1. Fare clic sul pulsante **Spedisci**. Viene visualizzata la pagina **Nuova spedizione**.
1. Fare clic sul pulsante **Invia spedizione**. Viene creata una spedizione.
1. Apri la spedizione appena creata.
1. Fare clic sul pulsante **Crea etichetta di spedizione**. Viene visualizzata la finestra di dialogo **Crea pacchetti**.

<u>Risultato previsto:</u>

Il pulsante **Aggiungi prodotti al pacchetto** nella finestra modale **Crea pacchetti** visualizza i campi con gli elementi dell&#39;ordine.

<u>Risultato effettivo:</u>

La finestra modale **Crea pacchetti** non è visualizzata correttamente. Impossibile aggiungere elementi dell&#39;ordine alla spedizione.

## Soluzione

Applichi la patch fornita in questo articolo.

## Patch

La patch è allegata a questo articolo. Per scaricarlo, scorri verso il basso fino alla fine dell’articolo e fai clic sul nome del file, oppure fai clic sul seguente collegamento:

[MC-35514-2.4.0-CE-compositore-2.patch](assets/MC-35514-2.4.0-CE-composer-2.patch.zip)

La patch è disponibile anche per il download nei formati `.git` e `.composer` nella pagina [Download di Adobe Commerce](https://magento.com/tech-resources/download), in **Patch** nella barra di navigazione a sinistra. Cercare la patch MC-35514.

### Versioni compatibili di Adobe Commerce:

La patch è stata creata per:

* Adobe Commerce su infrastruttura cloud versione 2.4.0
* Adobe Commerce on-premise versione 2.4.0

## Come applicare il cerotto

Per istruzioni, vedere [Come applicare una patch del compositore fornita dall&#39;Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md).

## File allegati
