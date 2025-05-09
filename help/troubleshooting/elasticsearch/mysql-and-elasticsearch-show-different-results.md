---
title: MySQL e Elasticsearch mostrano risultati diversi
description: Questo articolo fornisce una patch per il problema noto di Adobe Commerce on cloud infrastructure 2.2.3 relativo all’ottenimento di risultati di ricerca diversi per la stessa query di ricerca con MySQL e Elasticsearch.
exl-id: 37a0164a-0237-4200-ab9c-e0dbad7e2062
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# MySQL e Elasticsearch mostrano risultati diversi

>[!WARNING]
>
> [Il motore di ricerca del catalogo MySQL verrà rimosso in Adobe Commerce 2.4.0](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md). Prima di installare la versione 2.4.0, è necessario aver configurato e configurato l’host di Elasticsearch. Consulta [Installa e configura Elasticsearch](https://experienceleague.adobe.com/it/docs/commerce-operations/configuration-guide/search/overview-search) nella documentazione per gli sviluppatori.

Questo articolo fornisce una patch per il problema noto di Adobe Commerce on cloud infrastructure 2.2.3 relativo all’ottenimento di risultati di ricerca diversi per la stessa query di ricerca con MySQL e Elasticsearch.

## Problema:

I risultati della ricerca nel catalogo con lo stesso set di filtri variano a seconda del motore di ricerca utilizzato, MySQL o Elasticsearch.

<u>Passaggi da riprodurre</u>:

1. Installa e configura Elasticsearch.
1. Nella vetrina, seleziona uno dei filtri.
1. Prendi nota del numero di prodotti corrispondenti.
1. Configura la [ricerca MySQL predefinita](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md).
1. Nella vetrina, seleziona uno dei filtri.
1. Prendi nota del numero di prodotti corrispondenti.

<u>Risultato previsto</u>:
Il numero di prodotti corrispondenti è lo stesso.

<u>Risultato effettivo</u>:
Il numero di prodotti corrispondenti è diverso.

## Patch

Le patch sono allegate a questo articolo. Per scaricare una patch, scorri verso il basso fino alla fine dell’articolo e fai clic sul nome del file richiesto, oppure fai clic sui seguenti collegamenti:

[Scarica MDVA-12312\_EE\_2.2.3\_COMPOSER\_v1.patch](assets/MDVA-12312_EE_2.2.3_COMPOSER_v1.patch.zip)

[Scarica MDVA-14172\_EE\_2.2.6\_COMPOSER\_v1.patch](assets/MDVA-14172_EE_2.2.6_COMPOSER_v1.patch.zip)

### Versioni compatibili di Adobe Commerce:

Le patch sono state create per:

* Adobe Commerce su infrastruttura cloud 2.2.3 (il file `MDVA-12312_EE_2.2.3_COMPOSER_v1.patch`)
* Adobe Commerce su infrastruttura cloud 2.2.6 (il file `MDVA-14172_EE_2.2.6_COMPOSER_v1.patch`)

La patch `MDVA-12312_EE_2.2.3_COMPOSER_v1.patch` è compatibile (ma potrebbe non risolvere il problema) anche con le seguenti versioni ed edizioni di Adobe Commerce:

* Adobe Commerce sull’infrastruttura cloud 2.2.4
* Adobe Commerce sull’infrastruttura cloud 2.2.5
* Adobe Commerce on-premise 2.2.3
* Adobe Commerce on-premise 2.2.4
* Adobe Commerce on-premise 2.2.5

La patch `MDVA-14172_EE_2.2.6_COMPOSER_v1.patch` è compatibile (ma potrebbe non risolvere il problema) anche con le seguenti versioni ed edizioni di Adobe Commerce:

* Adobe Commerce on-premise 2.2.6

## Come applicare il cerotto

Per istruzioni, consulta [Come applicare una patch del compositore fornita da Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) nella Knowledge Base di supporto.

## File allegati
