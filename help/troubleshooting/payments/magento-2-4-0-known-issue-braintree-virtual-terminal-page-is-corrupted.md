---
title: Pagina Braintree terminale virtuale Adobe Commerce 2.4.0 danneggiata
description: Questo articolo fornisce una patch per il problema noto di Adobe Commerce 2.4.0, in cui la pagina Braintree terminale virtuale non carica gli elementi dell’interfaccia utente corretti o un messaggio di errore corretto se Braintree non è configurato.
exl-id: 1d4d762d-2ab3-4752-ad6d-1eb6a179917d
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# Pagina Braintree terminale virtuale Adobe Commerce 2.4.0 danneggiata

Questo articolo fornisce una patch per il problema noto di Adobe Commerce 2.4.0, in cui la pagina Braintree terminale virtuale non carica gli elementi dell’interfaccia utente corretti o un messaggio di errore corretto se Braintree non è configurato.

## Prodotti e versioni interessati

* Adobe Commerce on-premise 2.4.0
* Adobe Commerce sull’infrastruttura cloud 2.4.0

## Problema

### Scenario 1: il metodo di pagamento Braintree è configurato

<u>Passaggi da riprodurre:</u>

In Commerce Admin, vai a **Vendite** > **Braintree terminale virtuale** . **&#x200B; &#x200B;**

<u>Risultato previsto:</u>

La pagina **Braintree terminale virtuale** viene caricata con l&#39;interfaccia utente corretta.

<u>Risultato effettivo:</u>

L&#39;interfaccia utente della pagina **Braintree terminale virtuale** è interrotta.

### Scenario 2: il metodo di pagamento Braintree è configurato

<u>Passaggi da riprodurre:</u>

In Commerce Admin, vai a **Vendite** > **Braintree terminale virtuale** . **&#x200B; &#x200B;**

<u>Risultato previsto:</u>

La pagina **Braintree terminale virtuale** viene caricata con l&#39;interfaccia utente corretta e viene visualizzato un avviso che informa che Braintree non è ancora configurato.

<u>Risultato effettivo:</u>

L&#39;interfaccia utente della pagina **Braintree terminale virtuale** è interrotta e non viene visualizzato alcun avviso.

## Soluzione

Applichi la patch fornita in questo articolo.

## Patch

La patch è allegata a questo articolo. Per scaricarlo, scorri verso il basso fino alla fine dell’articolo e fai clic sul nome del file, oppure fai clic sul seguente collegamento:

[BUNDLE-2670-composer.patch](assets/BUNDLE-2670-composer.patch.zip)

### Versioni compatibili di Adobe Commerce:

La patch è stata creata per:

* Adobe Commerce sull’infrastruttura cloud 2.4.0
* Adobe Commerce on-premise 2.4.0

## Come applicare il cerotto

Per istruzioni, vedere [Come applicare una patch del compositore fornita dall&#39;Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md).

## File allegati
