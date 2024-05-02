---
title: Prestazioni API e del sito ridotte
description: Questo articolo fornisce una patch per il problema noto di Adobe Commerce on cloud infrastructure 2.2.1 relativo ad avere un sito basso e prestazioni API causate da un lungo tempo richiesto per scrivere "debug.log".
exl-id: b71816cd-f580-4c80-9694-585ed051a56d
feature: REST, Observability
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# Prestazioni API e del sito ridotte

Questo articolo fornisce una patch per il problema noto di Adobe Commerce on cloud infrastructure 2.2.1 relativo alle basse prestazioni di siti e API causate dal lungo tempo richiesto per la scrittura `debug.log`.

## Problema

Le prestazioni del sito sono lente. Le operazioni API vengono eseguite lentamente, ad esempio aggiornando i prodotti tramite `PUT` metodo. Se si analizzano più da vicino le operazioni che utilizzano New Relic, la maggior parte della memoria e della CPU viene utilizzata per la scrittura in `/var/log/debug.log`.

## Soluzione

Per risolvere il problema, applicare la patch. La patch suddivide e scrive i log dei metodi di log, pagamento e spedizione in file separati.

## Patch

La patch è allegata a questo articolo. Per scaricarlo, scorri verso il basso fino alla fine dell’articolo e fai clic sul nome del file o sul seguente collegamento:

[Scarica MDVA-8371\_EE\_2.2.1\_COMPOSER\_v2.patch](assets/MDVA-8371_EE_2.2.1_COMPOSER_v2.patch.zip)

### Versioni compatibili di Adobe Commerce

La patch è stata creata per:

* Adobe Commerce sull’infrastruttura cloud 2.2.1

La patch è compatibile (ma potrebbe non risolvere il problema) anche con le seguenti versioni di Adobe ed edizioni:

* Adobe Commerce sull’infrastruttura cloud 2.2.0, 2.2.2, 2.2.3
* Adobe Commerce on-premise 2.2.0, 2.2.2, 2.2.3

## Come applicare il cerotto

Consulta [Come applicare una patch del compositore fornita da Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) nella knowledge base di supporto per le istruzioni.

## File allegati
