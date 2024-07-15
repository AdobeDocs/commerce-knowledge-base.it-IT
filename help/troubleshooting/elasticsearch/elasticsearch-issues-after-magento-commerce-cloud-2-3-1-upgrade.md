---
title: Problemi di Elasticsearch dopo l’aggiornamento all’infrastruttura cloud Adobe Commerce 2.3.1+
description: Questo articolo illustra una correzione dei problemi durante la distribuzione dopo l’aggiornamento ad Adobe Commerce sulle versioni 2.3.1 e successive dell’infrastruttura cloud, se utilizzi le versioni 2.x e 5.x di Elasticsearch.
exl-id: 6ceeb2ea-528d-4c03-ab2b-c5aed46fd0a2
feature: Cloud
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 0%

---

# Problemi di Elasticsearch dopo l’aggiornamento all’infrastruttura cloud Adobe Commerce 2.3.1+

>[!WARNING]
>
>[Il motore di ricerca del catalogo MySQL verrà rimosso in Adobe Commerce 2.4.0](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md). Prima di installare la versione 2.4.0, è necessario aver configurato e configurato l’host Elasticsearch. Consulta [Installare e configurare Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html).

>[!WARNING]
>
>Gli aggiornamenti del servizio non possono essere inviati all’ambiente di produzione senza un preavviso di 48 ore lavorative al nostro team di infrastruttura. Ciò è necessario in quanto è necessario disporre di un tecnico del supporto dell&#39;infrastruttura per aggiornare la configurazione entro l&#39;intervallo di tempo desiderato, riducendo al minimo i tempi di inattività dell&#39;ambiente di produzione. Quindi, 48 ore prima del momento in cui le modifiche devono essere in produzione [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) specificando l&#39;aggiornamento del servizio richiesto e indicando l&#39;ora in cui desideri avviare il processo di aggiornamento.

Questo articolo illustra una correzione dei problemi durante la distribuzione dopo l’aggiornamento ad Adobe Commerce sulle versioni 2.3.1 e successive dell’infrastruttura cloud, se utilizzi le versioni 2.x e 5.x di Elasticsearch.

## Prodotti e versioni interessati:

* Adobe Commerce sull’infrastruttura cloud 2.3.1+
* Elasticsearch 2.x e articolo 5.x

## Causa

I commercianti che hanno effettuato l’aggiornamento ad Adobe Commerce sull’infrastruttura cloud (versioni 2.3.1 e successive) e che si trovano in una versione di Elasticsearch precedente alla 6.x possono riscontrare errori durante la distribuzione. Questo perché le versioni 2.x e 5.x di Elasticsearch sono [fine del ciclo di vita](https://www.elastic.co/support/eol) e non sono più supportate in Adobe Commerce. Il client Elasticsearch deve essere aggiornato oppure l’esecuzione di una distribuzione rischia di generare un errore. Per ulteriori informazioni, consulta [Modificare il client Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-downgrade.html) nella documentazione per gli sviluppatori.

## Problema

Durante la distribuzione viene visualizzato un messaggio di errore simile al seguente, che indica che la versione di Elasticsearch in uso non è compatibile: *La versione 5.2.2 del servizio Elasticsearch a livello di infrastruttura non è compatibile con la versione corrente del modulo elasticsearch/elasticsearch (6.7.0.0) utilizzato dall&#39;applicazione di Magento.* *È possibile risolvere il problema aggiornando il servizio Elasticsearch nell&#39;infrastruttura Magento Cloud alla versione 6.x*. Altri sintomi di questo problema possono essere la mancanza di immagini e problemi con i filtri nell’ambiente.

## Soluzione

>[!WARNING]
>
>Se disponi di un ambiente condiviso, assicurati che staging e produzione siano pronti per l’aggiornamento.

Per risolvere questo problema, il modulo client Elasticsearch e il servizio Elasticsearch devono utilizzare le versioni più recenti consigliate:

1. Segui le istruzioni per [modificare il modulo Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-downgrade.html) nella documentazione per gli sviluppatori in modo da disporre della versione più recente consigliata del modulo client Elasticsearch.
1. [Invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) e richiedi un aggiornamento del servizio Elasticsearch alla versione 6.x per staging e produzione. Tieni presente che il completamento di un aggiornamento al servizio Elasticsearch potrebbe richiedere un po’ di tempo.

## Lettura correlata

* [requisiti dello stack di tecnologia Adobe Commerce 2.3](https://devdocs.magento.com/guides/v2.3/install-gde/system-requirements-tech.html) nella documentazione per gli sviluppatori.
* [Configura il servizio Elasticsearch](https://devdocs.magento.com/cloud/project/project-conf-files_services-elastic.html) nella documentazione per gli sviluppatori.
* [Installa e configura Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html) nella documentazione per gli sviluppatori.
* [Assicurarsi che Elasticsearch sia installato correttamente](/help/troubleshooting/elasticsearch/ensure-elasticsearch-is-installed-properly.md) nella Knowledge Base di supporto.
