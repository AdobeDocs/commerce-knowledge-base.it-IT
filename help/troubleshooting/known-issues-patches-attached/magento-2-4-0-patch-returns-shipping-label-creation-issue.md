---
title: "patch di Adobe Commerce 2.4.0: restituisce il problema di creazione dell’etichetta di spedizione"
description: Questo articolo fornisce una patch per il problema noto di Adobe Commerce 2.4.0 quando si verifica un problema con la stampa di un’etichetta di spedizione per le restituzioni dei clienti.
exl-id: f78f8d7e-29e9-4d6c-83f6-cd5afa1d7d9c
feature: B2B, Orders, Returns, Communications, Shipping/Delivery
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# patch di Adobe Commerce 2.4.0: restituisce il problema di creazione dell’etichetta di spedizione

Questo articolo fornisce una patch per il problema noto di Adobe Commerce 2.4.0 quando si verifica un problema con la stampa di un’etichetta di spedizione per le restituzioni dei clienti.

## Prodotti e versioni interessati

* Adobe Commerce sull’infrastruttura cloud 2.4.0
* Adobe Commerce on-premise 2.4.0

## Problema

<u>Passaggi da riprodurre:</u>

1. Effettuare e completare un ordine con uno dei seguenti metodi di spedizione principali: FedEx, DHL, UPS e USPS.
1. Crea e autorizza restituzioni per questo ordine.
1. Aprire una pagina di **Informazioni sulla restituzione** autorizzata e fare clic sul pulsante **Crea etichetta di spedizione**.
1. Seleziona il metodo di spedizione, aggiungi un prodotto a un pacchetto e fai clic su Salva.

<u>Risultato previsto:</u>

Un&#39;etichetta di spedizione è stata creata e viene visualizzato un messaggio: *È stata creata un&#39;etichetta di spedizione.*

<u>Risultato effettivo:</u>

La pagina **Informazioni sulla restituzione** è interrotta e viene visualizzato un messaggio di errore nella pagina Informazioni sulla restituzione: *In questa sezione sono state apportate modifiche generali che non sono state salvate. Questa scheda contiene dati non validi*.

## Soluzione

Applica la [patch](assets/MC-35984-2.4.0-CE-composer.patch.zip) fornita in questo articolo.

## Patch

La patch è allegata a questo articolo. Per scaricarlo, scorri verso il basso fino alla fine dell’articolo e fai clic sul nome del file, oppure fai clic sul seguente collegamento:

[MC-35984-2.4.0-CE-compositore.patch](assets/MC-35984-2.4.0-CE-composer.patch.zip)

La patch è disponibile anche per il download nei formati `.git` e `.composer` nella pagina [Download di Adobe Commerce](https://magento.com/tech-resources/download), in **Patch** nella barra di navigazione a sinistra. Cercare la patch MC-35984.

## Come applicare il cerotto

Per istruzioni, vedere [Come applicare una patch del compositore fornita dall&#39;Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) nella pagina del supporto tecnico.

## Letture correlate nella knowledge base di supporto:

* [Problema noto di Adobe Commerce 2.4.0: visualizzazione dei dati dei messaggi non elaborati nella vetrina](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Problema noto di Adobe Commerce 2.4.0: l’esportazione delle aliquote fiscali non funziona](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problema noto di Adobe Commerce 2.4.0: il pulsante &quot;Aggiungi selezioni al carrello&quot; non funziona](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
* [Problema noto di Adobe Commerce 2.4.0: i metodi di pagamento Braintree non vengono visualizzati nel checkout di più indirizzi](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [L’amministratore B2B di Adobe Commerce 2.4.0 non può aggiungere un prodotto configurabile all’offerta](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Problema noto di Adobe Commerce 2.4.0: errore di visualizzazione degli ordini](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [Problema noto nella creazione di etichette di spedizione in Adobe Commerce 2.4.0](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
