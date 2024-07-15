---
title: Problemi di prestazioni causati da richieste Ajax eccessive
description: Questo articolo fornisce una patch per il problema noto relativo alle prestazioni di Adobe Commerce causato da un numero eccessivo di richieste Ajax. Il problema è stato risolto in Adobe Commerce 2.3.4.
exl-id: d9a69406-3970-4556-aa6a-1309b24366d8
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 0%

---

# Problemi di prestazioni causati da richieste Ajax eccessive

Questo articolo fornisce una patch per il problema noto relativo alle prestazioni di Adobe Commerce causato da un numero eccessivo di richieste Ajax. Il problema è stato risolto in Adobe Commerce 2.3.4.

## Problema

Adobe Commerce potrebbe inviare [richieste Ajax](/help/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.md) ridondanti dalla vetrina al server per ottenere le informazioni sul banner e sul cliente. Queste richieste Ajax hanno un impatto sulle prestazioni, soprattutto in condizioni di carico elevato (volume elevato e traffico elevato). Pertanto, se non si utilizza la funzionalità Banner, si consiglia di [disattivare completamente l&#39;output del modulo Banner di Adobe Commerce](/help/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.md) e applicare la patch per migliorare il recupero delle informazioni del cliente.

## Patch

La patch è allegata a questo articolo. Per scaricarlo, scorri verso il basso fino alla fine dell’articolo e fai clic sul nome del file o sul seguente collegamento:

[Scaricare MDVA-24597\_EE\_2.2.9\_COMPOSER\_v1.patch](assets/MDVA-24597_EE_2.2.9_COMPOSER_v1.patch.zip)

### Versioni compatibili di Adobe Commerce

La patch è valida per i seguenti prodotti e versioni:

* Adobe Commerce sull’infrastruttura cloud 2.2.9
* Adobe Commerce on-premise 2.2.9

Se disponi di una versione diversa di Adobe Commerce, valuta l’aggiornamento alla versione 2.3.x più recente. Se al momento questa non è un&#39;opzione, [contatta il supporto Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) e richiedi una patch per la tua versione.

## Come applicare il cerotto

Per istruzioni, vedere [Come applicare una patch del compositore fornita dall&#39;Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md).

## File allegati
