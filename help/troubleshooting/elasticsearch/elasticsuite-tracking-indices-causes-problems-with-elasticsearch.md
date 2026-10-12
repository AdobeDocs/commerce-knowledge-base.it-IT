---
title: Gli indici di tracciamento ElasticSuite causano problemi con Elasticsearch
description: Questo articolo parla del problema dei problemi di memoria di Elasticsearch causati dagli indici di tracciamento prodotti dal plug-in ElasticSuite.
exl-id: 67bfd06a-c801-4306-8510-a84a6fe5351a
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%
---
# Gli indici di tracciamento ElasticSuite causano problemi con Elasticsearch

>[!NOTE]
>
>ElasticSuite e le sue applicazioni affiliate sono strumenti di terze parti attualmente non supportati da Adobe. Questo contenuto viene presentato solo a scopo informativo e non come indicazione di ciò che è abilitato per la copertura del supporto.

Questo articolo parla del problema dei problemi di memoria di Elasticsearch causati dagli indici di tracciamento prodotti dal plug-in ElasticSuite.

## Prodotti e versioni interessati

Le versioni di ElasticSuite precedenti alla versione 2.8.0 non sono in grado di pulire periodicamente gli indici di tracciamento.

Le versioni di ElasticSuite precedenti alla 2.9.8 / 2.10.7 memorizzano gli indici di tracciamento negli indici giornalieri, il che provoca l’aumento del numero di indici aperti.

## Problema

Se è installato il plug-in di terze parti ElasticSuite, potrebbero verificarsi problemi di memoria di Elasticsearch e il servizio Elasticsearch potrebbe bloccarsi a causa di indici di tracciamento ElasticSuite. I sintomi includono:

* Elasticsearch si blocca senza errori di memoria.
* Durante l&#39;esecuzione di un comando di integrità `curl -m1 localhost:9200/_cluster/health?pretty` o `curl -m1 elasticsearch.internal:9200/_cluster/health?pretty` (per gli account di avvio) sono presenti centinaia o migliaia di `unassigned_shards`
* Le prestazioni di Elasticsearch o del sito sono gravemente peggiorate.
* *&quot;Nessun nodo attivo trovato nel cluster&quot;* in Elasticsearch deploy o log errors.
* *&quot;Rifiuto dell&#39;aggiornamento della mappatura a [&lt;\*>_tracking_ log_event_&lt;\*>]&quot;* in errori di distribuzione o di registro.

## Causa

ElasticSuite dispone di una nuova funzione che crea indici di tracciamento. Questi indici di tracciamento registrano quali termini di ricerca sono più utilizzati, quali termini generano il maggior fatturato e quali termini portano a una pagina di nessun risultato in modo che i commercianti possano creare sinonimi per correggerli. Non sembra eliminare gli indici di tracciamento, pertanto Elasticsearch esaurisce le risorse e subisce arresti anomali.

## Soluzione

### Aggiorna la versione di ElasticSuite per poter pulire periodicamente gli indici di tracciamento

Dopo aver aggiornato il plug-in ElasticSuite alla versione successiva alla 2.8.0, puoi configurare una pulizia periodica degli indici.

Vai a **Archivi** > **Configurazione** > **Tracciamento** > **Configurazione globale** > **Ritardo conservazione**

Il periodo di conservazione predefinito è di 365 giorni. Può ridurlo a 30 o 15 giorni.

### Aggiorna la versione di ElasticSuite per utilizzare indici mensili invece di indici giornalieri

Dopo aver aggiornato il plug-in ElasticSuite alla versione > 2.9.8 / 2.10.7, gli indici di tracciamento saranno basati su base mensile.

Puoi comunque ridurre il periodo di conservazione:

Vai a **Archivi** > **Configurazione** > **Tracciamento** > **Configurazione globale** > **Ritardo conservazione**

Il periodo di conservazione predefinito è di 12 mesi (genererà 12 indici). Può ridurla a 3 o 6 mesi.

### Utilizzare un processo cronologico per pulire i dati degli indici di tracciamento

Crea un processo cron per eliminare gli indici di tracciamento. Questo comando elimina gli indici creati nell&#39;ultimo mese:

```
   curl -XDELETE localhost:9200/<name in index> * **\_tracking\_log** * _$(date
    +'%Y%m' -d 'last month')*
```

Se desideri eliminare gli indici con una frequenza temporale impostata, crea un processo cron facendo riferimento ai seguenti articoli nella documentazione per sviluppatori:

* [Configurare un processo cron personalizzato e un gruppo cron (tutorial)](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/crons/custom-cron-tutorial)
* [Imposta processi cron](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property)
