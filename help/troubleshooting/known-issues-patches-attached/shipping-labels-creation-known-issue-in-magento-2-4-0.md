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

1. Apri l’ordine inserito nell’Amministratore, in **Vendite** > **Ordini**.
1. Fai clic su **Spedisci** pulsante. Il **Nuova spedizione** viene visualizzata la pagina.

<u>Risultato previsto:</u>

Il **Crea etichetta di spedizione** nella parte inferiore della pagina viene visualizzata una casella di controllo.

<u>Risultato effettivo:</u>

Il **Crea etichetta di spedizione** la casella di controllo non viene visualizzata.

### Scenario 2: creare un&#39;etichetta per la spedizione esistente

<u>Passaggi da riprodurre:</u>

1. Apri l’ordine inserito nell’Amministratore, in **Vendite** > **Ordini**.
1. Fai clic su **Spedisci** pulsante. Il **Nuova spedizione** viene visualizzata la pagina.
1. Fai clic su **Invia spedizione** pulsante. Viene creata una spedizione.
1. Apri la spedizione appena creata.
1. Fai clic su **Crea etichetta di spedizione** pulsante. Il **Crea pacchetti** viene visualizzata una finestra di dialogo.

<u>Risultato previsto:</u>

Il **Aggiungi prodotti al pacchetto** pulsante sulla **Crea pacchetti** nella finestra modale vengono visualizzati i campi con gli elementi dell’ordine.

<u>Risultato effettivo:</u>

Il **Crea pacchetti** finestra modale non viene visualizzata correttamente, non è possibile aggiungere articoli ordine alla spedizione.

## Soluzione

Applichi la patch fornita in questo articolo.

## Patch

La patch è allegata a questo articolo. Per scaricarlo, scorri verso il basso fino alla fine dell’articolo e fai clic sul nome del file, oppure fai clic sul seguente collegamento:

[MC-35514-2.4.0-CE-compositore-2.patch](assets/MC-35514-2.4.0-CE-composer-2.patch.zip)

La patch è disponibile anche per il download in entrambi, `.git` e `.composer`, formati su [Download di Adobe Commerce](https://magento.com/tech-resources/download) pagina, sotto **Patch** nella navigazione a sinistra della colonna. Cercare la patch MC-35514.

### Versioni compatibili di Adobe Commerce:

La patch è stata creata per:

* Adobe Commerce su infrastruttura cloud versione 2.4.0
* Adobe Commerce on-premise versione 2.4.0

## Come applicare il cerotto

Consulta [Come applicare una patch del compositore fornita dall&#39;Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) per istruzioni.

## File allegati
