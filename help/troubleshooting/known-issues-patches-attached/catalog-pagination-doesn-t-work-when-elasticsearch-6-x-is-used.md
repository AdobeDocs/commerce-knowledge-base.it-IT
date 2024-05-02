---
title: La paginazione del catalogo non funziona con Elasticsearch 6.x
description: Questo articolo fornisce una patch per il problema di Adobe Commerce per il quale la paginazione del catalogo non funziona su Elasticsearch 6.x.
exl-id: 60a423de-cf3a-4d73-a7cf-b6d9e95042ca
feature: Catalog Management, Categories, Search, Services
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# La paginazione del catalogo non funziona con Elasticsearch 6.x

Questo articolo fornisce una patch per il problema di Adobe Commerce per il quale la paginazione del catalogo non funziona su Elasticsearch 6.x.

La patch seguente risolve i problemi che gli utenti di Adobe Commerce 2.3.3 riscontrano nelle distribuzioni in cui Elasticsearch 6.x viene utilizzato come motore di ricerca nel catalogo. Gli utenti visualizzano un messaggio di errore quando tentano di spostarsi oltre la prima pagina dei risultati di ricerca.

Dopo l’installazione della patch, gli utenti potranno sfogliare tutti i risultati della ricerca.

## Prodotti e versioni interessati

* Adobe Commerce sull’infrastruttura cloud 2.3.3
* Adobe Commerce on-premise 2.3.3
* Magento Open Source 2.3.3
* Elasticsearch 6.x

## Problema

È stato rilevato un problema in Magento Open Source, Adobe Commerce on-premise e Adobe Commerce sull’infrastruttura cloud in cui l’impaginazione della pagina dei risultati della ricerca non funziona se passi da una pagina all’altra.

<u>Passaggi da riprodurre</u>:

1. Installa Adobe Commerce.
1. Abilita Elasticseach 6 come motore di ricerca catalogo.
1. Aggiungi alla categoria un numero di prodotti che supera il limite di 1 pagina impostato in Amministratore. **Nota**: 12 è il numero predefinito di prodotti visualizzati per pagina in Adobe Commerce 2.3.3.
1. Apri Categoria nella vetrina (risultati della ricerca o pagina della categoria) e vai a pagina 2.

<u>Risultato previsto</u>:

I prodotti devono essere visualizzati nella seconda pagina.

<u>Risultato effettivo</u>:

**&quot;***Impossibile trovare prodotti corrispondenti alla selezione***&quot;** viene visualizzato nella seconda pagina.

## Soluzione

Per risolvere il problema, applica la patch allegata a questo articolo. Per scaricarlo, scorri verso il basso fino alla fine dell’articolo e fai clic sul nome del file o sul seguente collegamento:

[Problema di paginazione del catalogo di download nella patch Elasticsearch 6.x](assets/Catalog_pagination_issue_on_Elasticsearch_6_composer-2019-10-11-08-07-41.patch.zip) - La patch è compatibile con tutte le versioni e le edizioni interessate.

>[!WARNING]
>
>L’Adobe consiglia vivamente di applicare il cerotto il prima possibile, anche se non ha manifestato alcun sintomo.

## Come applicare il cerotto

Consulta [Come applicare una patch del compositore fornita da Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) per istruzioni.

## File allegati
