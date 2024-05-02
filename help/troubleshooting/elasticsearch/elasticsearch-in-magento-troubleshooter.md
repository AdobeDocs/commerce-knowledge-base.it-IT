---
title: Elasticsearch di risoluzione dei problemi in Adobe Commerce
description: I problemi Elasticsearch su Adobe Commerce possono essere risolti utilizzando lo strumento di risoluzione dei problemi Elasticsearch. Fare clic su ogni domanda per visualizzare la risposta in ogni passaggio della risoluzione dei problemi.
exl-id: acae0da0-2918-4021-9fbe-c138940c5a72
feature: Categories
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '992'
ht-degree: 0%

---

# Elasticsearch di risoluzione dei problemi in Adobe Commerce

I problemi Elasticsearch su Adobe Commerce possono essere risolti utilizzando lo strumento di risoluzione dei problemi Elasticsearch. Fare clic su ogni domanda per visualizzare la risposta in ogni passaggio della risoluzione dei problemi.

>[!WARNING]
>
>Sull’infrastruttura cloud Adobe Commerce on, tieni presente che gli aggiornamenti dei servizi non possono essere inviati all’ambiente di produzione senza un preavviso di 48 ore lavorative al nostro team di infrastruttura. Ciò è necessario in quanto è necessario disporre di un tecnico del supporto dell&#39;infrastruttura per aggiornare la configurazione entro l&#39;intervallo di tempo desiderato, riducendo al minimo i tempi di inattività dell&#39;ambiente di produzione. Quindi 48 ore prima di quando le modifiche devono essere in produzione [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) specificare l&#39;aggiornamento del servizio richiesto e indicare l&#39;ora in cui si desidera avviare il processo di aggiornamento.

## Passaggio 1: verifica la presenza di un problema di Elasticsearch {#step-1}

+++**Il problema potrebbe essere legato all&#39;Elasticsearch?**

Elasticsearch di problemi indicati da messaggi di errore, &quot;_Nessun nodo attivo trovato nel cluster&quot;,_ i prodotti mancanti e la visualizzazione delle vecchie informazioni sui prodotti.

a. SÌ - Procedere come segue [Passaggio 2](#step-2).\
b. NO - Effettua nuovamente la ricerca utilizzando i termini di ricerca pertinenti nella [Knowledge base di Adobe Commerce Help Center](https://support.magento.com/hc).

+++

## Passaggio 2: verificare la presenza di un problema di installazione {#step-2}

+++**Si tratta di una nuova installazione di Elasticsearch?**

a. SÌ [Assicurati che Elasticsearch sia installato correttamente.](/help/troubleshooting/elasticsearch/ensure-elasticsearch-is-installed-properly.md) Controlla anche se ti trovi su Adobe Commerce on Cloud Infrastructure 2.3.1 o versione successiva. I commercianti che hanno effettuato l’aggiornamento ad Adobe Commerce sull’infrastruttura cloud (versioni 2.3.1 e successive) e che si trovano in una versione di Elasticsearch precedente alla 6.x possono riscontrare errori durante la distribuzione. Per risolvere questo problema, il modulo client Elasticsearch e il servizio Elasticsearch devono utilizzare le versioni più recenti consigliate. Per i passaggi, consulta [Problemi di Elasticsearch dopo l’aggiornamento a Adobe Commerce on cloud infrastructure 2.3.1+](/help/troubleshooting/elasticsearch/elasticsearch-issues-after-magento-commerce-cloud-2-3-1-upgrade.md).\
b. NO - Controllare l&#39;integrità del cluster. Se vi trovate in un ambiente di staging o produzione Pro, eseguite questo comando: `curl -m1 localhost:9200/_cluster/health?pretty`. Se ti trovi in un ambiente di integrazione (che include tutti i rami Starter), esegui `curl -m1 elasticsearch.internal:9200/_cluster/health?pretty`. Procedi a [Passaggio 3](#step-3).

+++

## Passaggio 3: verificare se il cluster Elasticsearch è disponibile {#step-3}

+++**Hai ricevuto una risposta dal servizio?**

a. SÌ - Procedere come segue [Passaggio 4](#step-4).\
b. NO - Procedi a [Passaggio 9](#step-9).

+++

## Passaggio 4: verificare che il cluster Elasticsearch sia integro {#step-4}

+++**Risposta verde?**

a. SÌ - È disponibile un Elasticsearch per l’elaborazione dei dati e la reindicizzazione dovrebbe funzionare. Procedi a [Passaggio 5](#step-5).\
b. NO - Giallo o rosso indica la presenza di problemi nelle connessioni tra nodi e alcuni dati potrebbero non essere disponibili. Se giallo, eseguire il comando: `php bin/magento config:show catalog/search/engine` per controllare il motore di ricerca. Procedi a [Passaggio 6](#step-6). Se rosso, [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Passaggio 5: verificare che la ricerca funzioni {#step-5}

+++**Problema di ricerca?**

I sintomi possono includere assenza di prodotti, categorie vuote o nessun aggiornamento di prodotti o categorie di prodotti non sono corretti.

a. YES - Eseguire questo comando per controllare lo stato della ricerca nel catalogo: `php bin/magento indexer:status`. Procedi a [Passaggio 8](#step-8).\
b. NO - Comando Esegui: `php bin/magento config:show catalog/search/engine`. Procedi a [Passaggio 6](#step-6).

+++

## Passaggio 6 - Controllare ElasticSuite {#step-6}

+++**ElasticSuite in uso?**

a. YES - Controllare se ElasticSuite è nella versione corrente eseguendo questo comando: `cat composer.lock | grep -A 1 elasticsuite | grep '"version"'` Per verificare se questa versione è obsoleta o consigliata, consulta [Github: Smile-SA/elaticsuite](https://github.com/Smile-SA/elasticsuite). Se ElasticSuite è aggiornato, procedi come segue: [Passaggio 10](#step-10).\
b. NO - passare a [Passaggio 7](#step-7).

+++

## Passaggio 7 - Controllare gli strumenti ECE aggiornati {#step-7}

+++**ECE-tools è la versione più recente?**

Esegui il comando: `php ./vendor/bin/ece-tools -V` e controllare la versione ECE-tools. È il [ultima versione di ECE-tools](https://github.com/magento/ece-tools/releases)?

a. SÌ - Procedere come segue [Fase 5a](#step-5).\
b. NO - Aggiornare gli strumenti ECE alla versione più recente. Esegui il comando `php bin/magento config: show catalog/search/engine` per controllare il motore di ricerca. Procedi a [Passaggio 6](#step-6).

+++

## Passaggio 8: verificare la reindicizzazione {#step-8}

+++**È lo stato di ricerca del catalogo in _Elaborazione_?**

a. SÌ - È necessario attendere fino al completamento dell’elaborazione e quindi verificare se le categorie di prodotti sono state aggiornate. In caso contrario, [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO - Se lo stato della ricerca nel catalogo è _Reindicizzazione richiesta_ esecuzione in CLI/Terminal: `php bin/magento cron:run`. In caso contrario, eseguire: `php bin/magento indexer:reindex`. Se il problema persiste, [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Passaggio 9: verificare la configurazione della password {#step-9}

+++**`.yaml`file aggiornato di recente?**

a. SÌ - Spunta `.yaml` Elasticsearch di configurazione con riferimento a DevDocs [Elasticsearch configurazione: per abilitare l’Elasticsearch](https://devdocs.magento.com/cloud/project/project-conf-files_services-elastic.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=elastic%20search%20yaml).\
b. N. - [Invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Passaggio 10: verificare la presenza di indici di tracciamento {#step-10}

+++**Sono elencati indici di tracciamento?**

Esegui `curl elasticsearch.internal:9200/_cat/indices` (se ti trovi in un ambiente di integrazione che include tutti i rami Starter ). Se vi trovate nell&#39;ambiente di staging o produzione Pro, eseguite `curl localhost:9200/_cat/indices`. Sono elencati indici di tracciamento? Controlla l’output per`_tracking_log_`.

a. SÌ - Se utilizzi una versione di ElasticSuite precedente alla versione 2.8.0, si consiglia di: [aggiornamento a ElasticSuite 2.8.0 per regolare la conservazione degli indici di tracciamento o disabilitare il tracciamento](https://support.magento.com/hc/en-us/articles/360035266131?). Se non è possibile eseguire immediatamente l&#39;aggiornamento, è possibile: [crea un cron per rimuovere gli indici di tracciamento](/help/troubleshooting/elasticsearch/elasticsuite-tracking-indices-causes-problems-with-elasticsearch.md). Tuttavia, questo potrebbe causare problemi di prestazioni. Dopo aver effettuato l’aggiornamento a ElasticSuite 2.8.0 o rimosso gli indici di tracciamento, esegui il comando (se ti trovi in ambienti di staging o produzione Pro):`localhost:9200/_cat/allocation?v` per verificare lo spazio disponibile. Se ti trovi in uno degli ambienti di integrazione (che include tutti i rami Starter), esegui `elasticsearch.internal:9200/_cat/allocation?v`. Procedi a [Passaggio 11](#step-11).\
b. NO - Se ti trovi in ambienti di staging o produzione Pro, esegui `localhost:9200/_cat/allocation?v` e verificare lo spazio disponibile. Se ti trovi in uno degli ambienti di integrazione (che include tutti i rami Starter), esegui `elasticsearch.internal:9200/_cat/allocation?v`. Procedi a [Passaggio 11](#step-11).

+++

## Passaggio 11: cercare un errore specifico {#step-11}

+++**Errore specifico?**

Registri di Adobe Commerce ed ES, estensioni e codice personalizzato.

a. SÌ - Consulta l’articolo Risoluzione dei problemi del Centro assistenza Adobe Commerce [Verificare che Elasticsearch sia installato correttamente](/help/troubleshooting/elasticsearch/ensure-elasticsearch-is-installed-properly.md) o [Elasticsearch di arresto anomalo o problemi di memoria insufficiente quando si utilizza il plug-in ElasticSuite](https://support.magento.com/hc/en-us/articles/360035266131).\
b. NO - Procedi a [Passaggio 12](#step-12).

+++

## Passaggio 12 - Controllare la memoria disponibile {#step-12}

+++**Utilizzo dello storage > 85%?**

a. SÌ - È necessario aumentare lo spazio di archiviazione disponibile. Consulta DevDocs[Elasticsearch configurazione: per abilitare l’Elasticsearch](https://devdocs.magento.com/cloud/project/project-conf-files_services-elastic.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=elastic%20search%20yaml). Quindi esegui: `localhost:9200/_cat/allocation?v` (se ti trovi in ambienti di staging o produzione Pro). Se ti trovi in uno degli ambienti di integrazione (che include tutti i rami Starter), esegui: `elasticsearch.internal:9200/_cat/allocation?v`. Procedi a [Passaggio 11](#step-11).\
b. N. - [Invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

[Torna al passaggio 1](#step-1)
