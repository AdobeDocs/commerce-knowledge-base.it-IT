---
title: Annullamento della validità della memorizzazione nella cache di Adobe Commerce su infrastruttura cloud v2.3.5 GraphQL non funziona
description: Questo articolo fornisce una patch per il problema in cui la richiesta "GET" di GraphQL restituisce informazioni obsolete se il cliente cambia le informazioni del prodotto.
exl-id: 10ae52bd-e71a-42e3-9600-7a9713903815
feature: GraphQL, Cache, Categories, Cloud, Paas
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# Annullamento della validità della memorizzazione nella cache di Adobe Commerce su infrastruttura cloud v2.3.5 GraphQL non funziona

Questo articolo fornisce una patch per il problema in cui GraphQL `GET` la richiesta restituisce informazioni obsolete se il cliente modifica le informazioni sul prodotto.

## Prodotti e versioni interessati

Adobe Commerce su infrastruttura cloud v2.3.5.

## Problema

Le richieste GraphQL vengono memorizzate nella cache da Fastly e la versione memorizzata nella cache viene recuperata per ogni richiesta successiva da Fastly. Quando un prodotto viene salvato nuovamente nel backend di Adobe Commerce, la cache Fastly deve essere invalidata quando un prodotto viene aggiornato. Tuttavia, rimane valida.

<u>Passaggi da riprodurre</u>:

1. Attiva la seguente richiesta GraphQL per ottenere prodotti per determinate categorie, ad esempio:
   <pre><magento2-server>
    </pre>
1. Salva nuovamente in Commerce Admin uno dei prodotti recuperati dalla richiesta precedente.
1. Attiva di nuovo la richiesta.

<u>Risultati previsti</u>:

Il `X-Cache` l’intestazione contiene `MISS`.

<u>Risultati effettivi</u>:

Il `X-Cache` l’intestazione contiene `HIT`, il che significa che la risposta è memorizzata nella cache.

## Soluzione

Disattiva la cache dei prodotti GraphQL con la patch fornita in questo articolo.

## Patch

La patch è allegata a questo articolo. Per scaricarlo, scorri verso il basso fino alla fine dell’articolo e fai clic sul nome del file o sul seguente collegamento:

[MDVA-28559\_EE\_2.3.5-p1\_COMPOSER\_v1.patch](assets/MDVA-28559_EE_2.3.5-p1_v1.composer.patch.zip)

### Versioni compatibili di Adobe Commerce:

La patch è stata creata per:

* Adobe Commerce su infrastruttura cloud v2.3.5

La patch è compatibile (ma potrebbe non risolvere il problema) anche con le seguenti versioni ed edizioni di Adobe Commerce:

* Adobe Commerce su infrastruttura cloud v2.4.0
* Adobe Commerce on-premise v2.4.0
* Adobe Commerce su infrastruttura cloud v2.3.5-p2
* Adobe Commerce on-premise v2.3.5-p2
* Adobe Commerce su infrastruttura cloud v2.3.5-p1
* Adobe Commerce on-premise v2.3.5-p1
* Adobe Commerce on-premise v2.3.5
* Adobe Commerce su infrastruttura cloud v2.3.4-p2
* Adobe Commerce on-premise v2.3.4-p2
* Adobe Commerce sull’infrastruttura cloud v2.3.4
* Adobe Commerce on-premise v2.3.4
* Adobe Commerce on-premise v2.3.3-p1
* Adobe Commerce on-premise v2.3.3

## Come applicare il cerotto

Consulta [Come applicare una patch del compositore fornita dall&#39;Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) per istruzioni su come applicare una patch del compositore.

## File allegati
