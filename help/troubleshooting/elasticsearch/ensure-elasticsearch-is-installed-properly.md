---
title: Verificare che Elasticsearch sia installato correttamente
description: Questo articolo illustra le soluzioni per i problemi causati da un'installazione e una configurazione non corrette degli Elasticsearch (ES).
exl-id: d2c5971c-4db4-4857-ae79-970313bce981
feature: Install
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# Verificare che Elasticsearch sia installato correttamente

Questo articolo illustra le soluzioni per i problemi causati da un&#39;installazione e una configurazione non corrette degli Elasticsearch (ES).

>[!WARNING]
>
>Sull’infrastruttura cloud Adobe Commerce on, tieni presente che gli aggiornamenti dei servizi non possono essere inviati all’ambiente di produzione senza un preavviso di 48 ore lavorative al nostro team di infrastruttura. Ciò è necessario in quanto è necessario disporre di un tecnico del supporto dell&#39;infrastruttura per aggiornare la configurazione entro l&#39;intervallo di tempo desiderato, riducendo al minimo i tempi di inattività dell&#39;ambiente di produzione. Quindi, 48 ore prima del momento in cui le modifiche devono essere in produzione, [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) specificando l&#39;aggiornamento del servizio richiesto e indicando l&#39;ora in cui desideri avviare il processo di aggiornamento.

## Elasticsearch di compatibilità della versione con Adobe Commerce

* Adobe Commerce on-premise e Adobe Commerce sull’infrastruttura cloud:
   * v2.2.3+ supporta ES 5.x
   * v2.2.8+ e v2.3.1+ supportano ES 6.x
   * ES v2.x e v5.x non sono consigliati a causa di [fine del ciclo di vita](https://www.elastic.co/support/eol). Tuttavia, se si dispone di Adobe Commerce v2.3.1 e si desidera utilizzare ES 2.x o ES 5.x, è necessario [Modificare il client php Elasticsearch](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/overview-search).
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

Dove *versione* è il servizio Elasticsearch in esecuzione nell&#39;ambiente cloud.

## Causa

L&#39;Elasticsearch non è installato correttamente. Ciò potrebbe essere dovuto a:

* Un errore di battitura nel file di configurazione.
* Versione del file di configurazione che non corrisponde a nessuna versione di Elasticsearch installata per l&#39;ambiente.
* Versione correttamente installata nell’ambiente, configurata correttamente nel file di configurazione, ma non supportata per la versione di Adobe Commerce attualmente installata.

## Soluzione

Per impostare correttamente l&#39;Elasticsearch:

* I commercianti su Adobe Commerce su infrastruttura cloud possono seguire i passaggi descritti nella documentazione per gli sviluppatori: [Configurazione del servizio Elasticsearch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch).
* I commercianti di Adobe Commerce on-premise e Magento Open Source possono seguire i passaggi descritti nella documentazione per gli sviluppatori: [Installa e configura Elasticsearch](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/overview-search).

Dopo aver configurato l’Elasticsearch, verifica che sia configurato correttamente:

1. Accedi al server.
1. Controllare il numero di versione dell&#39;Elasticsearch (2.x, 5.x o 6.x) nell&#39;output dell&#39;esecuzione del comando: `curl -XGET <Elasticsearch hostname>:<Elasticsearch server port>` Ad esempio, in Adobe Commerce sull&#39;infrastruttura cloud: `curl -XGET localhost:9200`
1. Controllare la configurazione in Adobe Commerce nella configurazione dell&#39;infrastruttura cloud eseguendo il comando: `php bin/magento config:show catalog/search`
1. Controllare `catalog/search/engine` e assicurarsi che corrisponda al numero di versione Elasticsearch. Ad esempio, in Adobe Commerce sull’infrastruttura cloud:
   * Elasticsearch 5.X - ricerca elastica5
   * Elasticsearch 6.X - ricerca elastica6
   * Elasticsearch 2.X - ricerca elastica
1. Seleziona `index_prefix`. Se disponi di più ambienti, assicurati di disporre di valori `index_prefix` diversi.
