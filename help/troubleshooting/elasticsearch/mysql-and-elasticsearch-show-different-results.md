---
title: MySQL e Elasticsearch mostrano risultati diversi
description: Questo articolo fornisce una patch per il problema noto di Adobe Commerce on cloud infrastructure 2.2.3 relativo all’ottenimento di risultati di ricerca diversi per la stessa query di ricerca con MySQL e Elasticsearch.
exl-id: 37a0164a-0237-4200-ab9c-e0dbad7e2062
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# MySQL e Elasticsearch mostrano risultati diversi

>[!WARNING]
>
> [Il motore di ricerca del catalogo MySQL verrà rimosso in Adobe Commerce 2.4.0](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md). Prima di installare la versione 2.4.0, è necessario aver configurato e configurato l’host di Elasticsearch. Fai riferimento a [Installare e configurare Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html) nella documentazione per gli sviluppatori.

Questo articolo fornisce una patch per il problema noto di Adobe Commerce on cloud infrastructure 2.2.3 relativo all’ottenimento di risultati di ricerca diversi per la stessa query di ricerca con MySQL e Elasticsearch.

## Problema:

I risultati della ricerca nel catalogo con lo stesso set di filtri variano a seconda del motore di ricerca utilizzato, MySQL o Elasticsearch.

<u>Passaggi da riprodurre</u> :

1. Installa e configura Elasticsearch.
1. Nella vetrina, seleziona uno dei filtri.
1. Prendi nota del numero di prodotti corrispondenti.
1. Configura il predefinito [Ricerca MySQL](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md).
1. Nella vetrina, seleziona uno dei filtri.
1. Prendi nota del numero di prodotti corrispondenti.

<u>Risultato previsto</u>: il numero di prodotti corrispondenti è lo stesso.

<u>Risultato effettivo</u>: il numero di prodotti corrispondenti è diverso.

## Patch

Le patch sono allegate a questo articolo. Per scaricare una patch, scorri verso il basso fino alla fine dell’articolo e fai clic sul nome del file richiesto, oppure fai clic sui seguenti collegamenti:

[Scarica MDVA-12312\_EE\_2.2.3\_COMPOSER\_v1.patch](assets/MDVA-12312_EE_2.2.3_COMPOSER_v1.patch.zip)

[Scarica MDVA-14172\_EE\_2.2.6\_COMPOSER\_v1.patch](assets/MDVA-14172_EE_2.2.6_COMPOSER_v1.patch.zip)

### Versioni compatibili di Adobe Commerce:

Le patch sono state create per:

* Adobe Commerce sull’infrastruttura cloud 2.2.3 (il `MDVA-12312_EE_2.2.3_COMPOSER_v1.patch` file)
* Adobe Commerce sull’infrastruttura cloud 2.2.6 (il `MDVA-14172_EE_2.2.6_COMPOSER_v1.patch` file)

Il `MDVA-12312_EE_2.2.3_COMPOSER_v1.patch` La patch è compatibile (ma potrebbe non risolvere il problema) anche con le seguenti versioni ed edizioni di Adobe Commerce:

* Adobe Commerce sull’infrastruttura cloud 2.2.4
* Adobe Commerce sull’infrastruttura cloud 2.2.5
* Adobe Commerce on-premise 2.2.3
* Adobe Commerce on-premise 2.2.4
* Adobe Commerce on-premise 2.2.5

Il `MDVA-14172_EE_2.2.6_COMPOSER_v1.patch` La patch è compatibile (ma potrebbe non risolvere il problema) anche con le seguenti versioni ed edizioni di Adobe Commerce:

* Adobe Commerce on-premise 2.2.6

## Come applicare il cerotto

Consulta [Come applicare una patch del compositore fornita dall&#39;Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) nella knowledge base di supporto per le istruzioni.

## File allegati
