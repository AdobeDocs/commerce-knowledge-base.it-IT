---
title: Le pagine di estrazione non vengono caricate quando ad blocker è abilitato
description: Questo articolo fornisce una patch per il problema noto di Adobe Commerce on cloud infrastructure 2.2.2 relativo al mancato caricamento delle pagine di pagamento causato da uBlock o altri ad blocker.
exl-id: fe718f21-df23-4ab1-a6b0-03bad4d7095d
feature: Checkout, Orders
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---

# Le pagine di estrazione non vengono caricate quando ad blocker è abilitato

Questo articolo fornisce una patch per il problema noto di Adobe Commerce on cloud infrastructure 2.2.2 relativo al mancato caricamento delle pagine di pagamento causato da uBlock o altri ad blocker.

## Problema

Se per l&#39;archivio sono abilitate le Google Analytics, quando un cliente con uBlock o un altro ad blocker installato procede all&#39;estrazione, il caricamento del file `trackingCode.js` viene bloccato e RequireJS interrompe il flusso di esecuzione JS. Questo causa problemi nel caricamento della pagina di pagamento.

<u>Passaggi da riprodurre</u>:

Prerequisiti: un ad blocker deve essere installato e attivo nel browser.

1. In Commerce Admin, abilita e configura la funzionalità Google Analytics.
1. Apri una pagina di prodotto nella vetrina.
1. Aggiungi prodotti al carrello.
1. Fare clic sul collegamento **Vai a estrazione**.

<u>Risultato previsto</u>: la pagina di estrazione viene caricata e il cliente può completare l&#39;estrazione.

<u>Risultato effettivo</u>: la pagina di estrazione non viene caricata; lo spinner di caricamento non scompare mai.

## Patch

La patch è allegata a questo articolo. Per scaricarlo, scorri verso il basso fino alla fine dell’articolo e fai clic sul nome del file, oppure fai clic sul seguente collegamento:

[Scarica MDVA-9353\_EE\_2.2\_v1.compositore.patch](assets/MDVA-9353_EE_2.2.2_v1.composer.patch.zip)

### Versioni compatibili di Adobe Commerce:

La patch è stata creata per:

* Adobe Commerce sull’infrastruttura cloud 2.2.2

La patch è compatibile (ma potrebbe non risolvere il problema) anche con le seguenti versioni ed edizioni di Adobe Commerce:

* Adobe Commerce sull’infrastruttura cloud dalla versione 2.1.0 alla versione 2.1.14
* Adobe Commerce sull’infrastruttura cloud da 2.2.0 a 2.2.1 e da 2.2.3 a 2.2.5
* Adobe Commerce on-premise dalla versione 2.1.0 al 2.1.14
* Adobe Commerce on-premise da 2.2.0 a 2.2.5

## Come applicare il cerotto

Per istruzioni, vedere [Come applicare una patch del compositore fornita dall&#39;Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) nella Knowledge Base di supporto.

## Collegamenti utili

* [Il problema discusso su GitHub](https://github.com/magento/magento2/pull/13061)

## File allegati
