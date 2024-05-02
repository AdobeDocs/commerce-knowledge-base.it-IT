---
title: Verificare che Elasticsearch sia installato correttamente
description: Questo articolo illustra le soluzioni per i problemi causati da un'installazione e una configurazione non corrette degli Elasticsearch (ES).
exl-id: d2c5971c-4db4-4857-ae79-970313bce981
feature: Install
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# Verificare che Elasticsearch sia installato correttamente

Questo articolo illustra le soluzioni per i problemi causati da un&#39;installazione e una configurazione non corrette degli Elasticsearch (ES).

>[!WARNING]
>
>Sull’infrastruttura cloud Adobe Commerce on, tieni presente che gli aggiornamenti dei servizi non possono essere inviati all’ambiente di produzione senza un preavviso di 48 ore lavorative al nostro team di infrastruttura. Ciò è necessario in quanto è necessario disporre di un tecnico del supporto dell&#39;infrastruttura per aggiornare la configurazione entro l&#39;intervallo di tempo desiderato, riducendo al minimo i tempi di inattività dell&#39;ambiente di produzione. Quindi 48 ore prima di quando le modifiche devono essere in produzione, [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) specificare l&#39;aggiornamento del servizio richiesto e indicare l&#39;ora in cui si desidera avviare il processo di aggiornamento.

## Elasticsearch di compatibilità della versione con Adobe Commerce

* Adobe Commerce on-premise e Adobe Commerce sull’infrastruttura cloud:
   * v2.2.3+ supporta ES 5.x
   * v2.2.8+ e v2.3.1+ supportano ES 6.x
   * ES v2.x e v5.x non sono consigliati a causa di [Fine del ciclo di vita](https://www.elastic.co/support/eol). Tuttavia, se disponi di Adobe Commerce v2.3.1 e desideri utilizzare ES 2.x o ES 5.x, devi [Cambia il client php di Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-downgrade.html).
* Il Magento Open Source v2.3.0+ supporta ES 5.x e 6.x (ma si consiglia 6.x).

## Problema

I seguenti sintomi indicano che l’Elasticsearch non è configurato correttamente:

* `Error: No alive nodes in your cluster` - questo errore può essere visualizzato nei registri di Adobe Commerce:
   * `var/log/system.log`
   * `var/log/support_report.log`
   * `var/log/cron.log`
   * `var/log/exception.log`
   * oppure al prompt (ad esempio, quando esegui una reindicizzazione)
* Errori che indicano che la versione dell’Elasticsearch non è compatibile con la versione corrente di Adobe Commerce (si tratta di un errore specifico di Adobe Commerce sull’infrastruttura cloud):

  ```
  [YYYY-MM-DD HH:MM:SS] CRITICAL: Fix configuration with given suggestions:    - Elasticsearch version #<version> is not compatible with current version of magento    Upgrade elasticsearch version to ~5.0
  ```

Dove *version* è il servizio Elasticsearch in esecuzione nell’ambiente cloud.

## Causa

L&#39;Elasticsearch non è installato correttamente. Ciò potrebbe essere dovuto a:

* Un errore di battitura nel file di configurazione.
* Versione del file di configurazione che non corrisponde a nessuna versione di Elasticsearch installata per l&#39;ambiente.
* Versione correttamente installata nell’ambiente, configurata correttamente nel file di configurazione, ma non supportata per la versione di Adobe Commerce attualmente installata.

## Soluzione

Per impostare correttamente l&#39;Elasticsearch:

* I commercianti su Adobe Commerce su infrastruttura cloud possono seguire i passaggi descritti nella documentazione per gli sviluppatori: [Configura servizio Elasticsearch](https://devdocs.magento.com/guides/v2.3/cloud/project/project-conf-files_services-elastic.html).
* I commercianti on-premise e di Magento Open Source di Adobe Commerce possono seguire i passaggi descritti nella documentazione per gli sviluppatori: [Installare e configurare Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html).

Dopo aver configurato l’Elasticsearch, verifica che sia configurato correttamente:

1. Accedi al server.
1. Verifica il numero di versione dell’Elasticsearch (2.x, 5.x o 6.x) nell’output di esecuzione del comando: `curl -XGET <Elasticsearch hostname>:<Elasticsearch server port>` Ad esempio, in Adobe Commerce sull’infrastruttura cloud: `curl -XGET localhost:9200`
1. Controlla cosa è configurato in Adobe Commerce nella configurazione dell’infrastruttura cloud eseguendo il comando: `php bin/magento config:show catalog/search`
1. Verifica `catalog/search/engine` e assicurati che corrisponda al numero di versione Elasticsearch. Ad esempio, in Adobe Commerce sull’infrastruttura cloud:
   * Elasticsearch 5.X - ricerca elastica5
   * Elasticsearch 6.X - ricerca elastica6
   * Elasticsearch 2.X - ricerca elastica
1. Verifica `index_prefix`. Se disponi di più ambienti, assicurati di disporre di diversi `index_prefix` per loro.
