---
title: Collo di bottiglia di MySQL ad alto carico in Adobe Commerce sull’infrastruttura cloud
description: Questo argomento descrive una soluzione quando un carico elevato da MySQL causa un problema di collo di bottiglia delle prestazioni in Adobe Commerce sull’infrastruttura cloud.
exl-id: c1f9d282-41d8-4850-8a24-336d55aa3140
feature: Cloud, Observability, Paas, Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '864'
ht-degree: 0%

---

# Collo di bottiglia di MySQL ad alto carico in Adobe Commerce sull’infrastruttura cloud

Questo argomento descrive una soluzione quando un carico elevato da MySQL causa un problema di collo di bottiglia delle prestazioni in Adobe Commerce sull’infrastruttura cloud.

## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud 2.x.x, account Pro.

### Prerequisiti

* ECE Tools versione 2002.0.16 e successive
* Servizio New Relic APM (**L&#39;account Adobe Commerce sull&#39;infrastruttura cloud include il software per il servizio New Relic APM** insieme a una chiave di licenza.)

Per ulteriori informazioni sul servizio New Relic APM e sulla relativa configurazione con l&#39;account Adobe Commerce sull&#39;infrastruttura cloud, vedere [Servizi New Relic](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/monitor/new-relic/new-relic-service) e [Introduzione a New Relic APM](https://docs.newrelic.com/docs/apm/new-relic-apm/getting-started/introduction-apm/).

## Problema

<u>Passaggi Per Verificare Se Il Problema Ti Interessa</u>

1. Nel grafico di panoramica di New Relic APM, verificare che MySQL sia diventato un collo di bottiglia. Vedere l&#39;immagine di esempio seguente in cui MySQL è diventato un collo di bottiglia e richiede la maggior parte del tempo delle transazioni Web:

   ![KB-372_image002.png](assets/KB-372_image002.png)

   Si noti come la linea tratteggiata rossa nell&#39;immagine mostri una tendenza verso l&#39;alto distinguibile nel tempo delle transazioni Web MySQL e quindi picchi a livelli ancora più alti.
1. Da qui è possibile passare alla schermata **Database** in cui è possibile visualizzare la seconda indicazione di un throughput elevato o di query `SELECT` lente in MySQL e nell&#39;immagine di esempio seguente è possibile vedere quando si ordina in base a **Più dispendioso in termini di tempo**, l&#39;archivio, in questo esempio, è lento per `SELECT` query MySQL.

   ![KB-372_image003_BlurredExtension.png](assets/KB-372_image003_BlurredExtension.png)

Analizzare le transazioni lente in New Relic APM. Se il volume di query o la pressione su un database MySQL è elevato, è possibile distribuire il carico tra nodi diversi abilitando `SLAVE` connessioni.

## Causa

Il tuo archivio Adobe Commerce sull&#39;infrastruttura cloud ha un throughput elevato o è lento per `SELECT` query MySQL.

## Soluzione

>[!WARNING]
>
>Per l&#39;architettura scalata (architettura divisa), le connessioni slave Redis **NON DEVONO** essere abilitate. Per verificare se l&#39;architettura è scalata, vai all&#39;URL del progetto, ad esempio `https://console.adobecommerce.com/<owner-user-name>/<project-ID>/<environment-name>`. Fai clic su **[!UICONTROL SSH]**. Se sono presenti più di tre nodi, l’architettura è in scala. Se abiliti Redis Slave Reads su architettura scalata, il cliente riceverà errori quando le connessioni Redis non sono in grado di connettersi. Questo ha a che fare con il modo in cui i cluster sono configurati per elaborare le connessioni Redis. Gli schiavi Redis sono ancora attivi ma non verranno utilizzati per Redis Reads. Per l’architettura scalata si consiglia di utilizzare Adobe Commerce 2.3.5 o versione successiva e implementare la nuova configurazione back-end Redis e implementare il caching L2 per Redis.

Se si verificano queste due indicazioni, l&#39;abilitazione delle connessioni `SLAVE` per il database MySQL e Redis può aiutare a distribuire il carico tra nodi diversi.

Adobe Commerce può leggere più database o Redis in modo asincrono. Aggiornamento del file `.magento.env.yaml` impostando su `true` i valori `MYSQL_USE_SLAVE_CONNECTION` e `REDIS_USE_SLAVE_CONNECTION` per utilizzare una connessione **di sola lettura** al database per ricevere traffico di sola lettura su un nodo non principale. Ciò migliora le prestazioni tramite il bilanciamento del carico, in quanto solo un nodo deve gestire il traffico di lettura-scrittura. Impostare su `false` per rimuovere qualsiasi array di connessione di sola lettura esistente dal file `env.php`.

### Passaggi

1. Modifica il file `.magento.env.yaml` e aggiungi il seguente contenuto:

   ![KB-372_image004.png](assets/KB-372_image004.png)

   Ulteriori dettagli sono disponibili in [Distribuire variabili in DevDocs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#mysql_use_slave_connection).

1. Apporta le modifiche e le invia in push.
1. Il push delle modifiche avvierà un nuovo processo di distribuzione. Una volta completata la distribuzione, l’istanza di Adobe Commerce sull’infrastruttura cloud ora deve essere configurata per l’utilizzo di connessioni slave.

## Domande comuni

Di seguito sono riportate le domande comuni che potresti porre quando prendi in considerazione l’utilizzo della funzionalità Connessioni slave per l’archivio dell’infrastruttura cloud di Adobe Commerce.

* Esistono problemi noti o limitazioni all’utilizzo delle connessioni slave? **Non sono stati rilevati problemi durante l&#39;utilizzo delle connessioni slave. Assicurati di utilizzare il pacchetto di strumenti ece aggiornato più di recente. Le istruzioni sono disponibili qui in [come aggiornare il pacchetto ece-tools](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package).**
* Esiste una latenza aggiuntiva con l’utilizzo delle connessioni slave? *Sì, la latenza cross-AZ (cross-Availability Zones) è più elevata e riduce le prestazioni di un&#39;istanza Adobe Commerce sull&#39;infrastruttura cloud nel caso in cui l&#39;istanza non sia sovraccarica e possa sopportare l&#39;intero carico. Tuttavia, se l&#39;istanza è sovraccarica, master-slave contribuirà alle prestazioni distribuendo il carico sul database MySQL o Redis tra nodi diversi.*

  **Nei cluster non sovraccaricati** - **Le connessioni slave rallenteranno le prestazioni del 10-15%**, che è uno dei motivi per cui non è predefinito.

  *Nei cluster con sovraccarico, tuttavia, si verifica un aumento delle prestazioni perché questi 10-15% vengono mitigati riducendo il carico dal traffico.*
* È necessario attivare queste impostazioni per il negozio? *Se il carico è elevato o si prevede un carico elevato sul database MySQL o Redis, è assolutamente necessario abilitare le connessioni slave. Per un cliente normale con traffico medio, questa è&#x200B;**not**un&#39;impostazione ottimale da abilitare.*

## Lettura correlata

Nella documentazione per gli sviluppatori:

* [Distribuisci variabili](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy).
* [Imposta replica database facoltativa](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/storage/split-db/multi-master-replication).
* [pacchetto ece-tools](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/package-overview).

>[!NOTE]
>
>Siamo consapevoli che questo articolo può ancora contenere termini software standard del settore che alcuni possono trovare razzisti, sessisti o oppressivi, e che possono far sentire il lettore ferito, traumatizzato, o sgradito. Adobe sta lavorando per rimuovere questi termini dal nostro codice, dalla nostra documentazione e dalle esperienze utente.
