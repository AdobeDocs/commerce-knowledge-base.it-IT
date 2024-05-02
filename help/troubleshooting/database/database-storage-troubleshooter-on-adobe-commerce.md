---
title: Risoluzione dei problemi di archiviazione del database su Adobe Commerce
description: Questo articolo è uno strumento di risoluzione dei problemi per i clienti che su Adobe Commerce hanno problemi con i database. Fare clic su ogni domanda per visualizzare la risposta in ogni passaggio della risoluzione dei problemi. A seconda dei sintomi e della configurazione, lo strumento di risoluzione dei problemi spiegherà come risolvere i problemi di spazio e configurazione con i database.
exl-id: f7b09023-7129-4fd0-9bb5-02a2228bc148
feature: Observability, Services, Storage, Support
role: Developer
source-git-commit: 324cce66df1e4ab7ec4ef8fb6512c3acbabdf3ab
workflow-type: tm+mt
source-wordcount: '813'
ht-degree: 0%

---

# Risoluzione dei problemi di archiviazione del database su Adobe Commerce

Questo articolo è uno strumento di risoluzione dei problemi per i clienti che su Adobe Commerce hanno problemi con i database. Fare clic su ogni domanda per visualizzare la risposta in ogni passaggio della risoluzione dei problemi. A seconda dei sintomi e della configurazione, lo strumento di risoluzione dei problemi spiegherà come risolvere i problemi di spazio e configurazione con i database.

## Passaggio 1: identificazione della directory con un problema di spazio {#step-1}

+++**Hai un `/tmp` problema causato dalla mancanza di spazio?**

Ciò può essere indicato da una serie di sintomi, tra cui `/tmp` il mount è pieno, il sito è inattivo o non è in grado di eseguire SSH in un nodo. Potresti anche riscontrare errori come _Spazio insufficiente sul dispositivo (28)_. Per un elenco degli errori risultanti da `/tmp` essere pieni, rivedere [/tmp montaggio pieno](/help/troubleshooting/miscellaneous/tmp-mount-full.md).

O hai un `/data/mysql` problema causato dalla mancanza di spazio? Questo può essere indicato anche da una varietà di sintomi, tra cui l’interruzione del sito, i clienti non in grado di aggiungere prodotti al carrello, l’errore di connessione al database e gli errori di Galeria come _SQLSTATE\[08S01\]: errore collegamento di comunicazione: 1047 WSREP_. Per un elenco degli errori derivanti da uno spazio su disco MySQL insufficiente, fare riferimento a [Spazio su disco MySQL insufficiente in Adobe Commerce sull’infrastruttura cloud](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md).

Se non si è sicuri di avere un problema di spazio su disco e si dispone di un account New Relic, passare alla [Pagina Host di monitoraggio dell&#39;infrastruttura New Relic](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/). Da qui, fai clic sul pulsante **Storage** , modificare il **Mostra grafico** da 5 a 20 risultati e cercare nella tabella per l&#39;uso di dischi elevati nel grafico o nella tabella Disk Used %. Per i passaggi più dettagliati, consulta [Monitoraggio dell&#39;infrastruttura New Relic > scheda Storage]https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#storage).

Se si verifica uno dei sintomi descritti in precedenza, controllare lo stato degli inodi per assicurarsi che non sia causato da un problema relativo al numero di file. A tale scopo, eseguire il comando seguente in CLI/Terminal:\
`df -ih`

L’IUse% è > 90%?

a. SÌ - La causa è un numero eccessivo di file. Rivedi i passaggi per rimuovere i file in modo sicuro in [Eliminazione sicura dei file quando lo spazio su disco è esaurito, Adobe Commerce sull’infrastruttura cloud](/help/troubleshooting/miscellaneous/safely-delete-files-when-out-of-disk-space-adobe-commerce-on-our-cloud-architecture.md). Procedi a [Passaggio 2](#step-2) dopo aver completato questi passaggi. Se vuoi richiedere più spazio, [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO - Controllare lo spazio. Esegui `df -h | grep mysql` e poi `df -h | grep tmp` nella CLI/Terminal per verificare l&#39;utilizzo dello spazio su disco nella `/tmp` e `/data/mysql` directory. Procedi a [Passaggio 3](#step-3).

+++

## Passaggio 2 - Controllare lo spazio su disco {#step-2}

+++**Verificare l&#39;utilizzo dello spazio su disco?**

Una volta ridotto il numero di file, eseguire `df -h | grep mysql` e poi `df -h | grep tmp` nella CLI/Terminal per verificare l&#39;utilizzo dello spazio su disco in `/tmp` e `/data/mysql`. È superiore al 70% utilizzato per `/tmp` o `/data/mysql`?

a. SÌ - Procedere come segue [Passaggio 3](#step-3).
b. NO - È possibile che le query stiano esaurendo lo spazio di archiviazione disponibile. Questo potrebbe causare l’arresto anomalo del nodo, causando l’interruzione della query e la rimozione di `tmp` file. Esamina l’output del `SHOW PROCESSLIST;` in MySQL CLI per le query che potrebbero essere la causa del problema. [Invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), per richiedere più spazio.

+++

## Passaggio 3: identificazione della directory con utilizzo elevato {#step-3}

+++**Quale directory è utilizzata per più del 70%?**

Quale directory è utilizzata per più del 70%? `/tmp` o `/data/mysql`?

>[!NOTE]
>
>Per impostazione predefinita, il timpdir del database scrive in `/tmp`. Per verificare che la configurazione del database sia ancora impostata su questo valore predefinito, eseguire il comando seguente in MySQL CLI: `SHOW VARIABLES LIKE "TMPDIR";` Se il timpdir del database scrive ancora in `/tmp`, visualizzerai `/tmp` nella colonna Valore.

a. `/tmp` - Procedi a [Passaggio 4](#step-4). \
b. `/data/mysql` - Procedi a [Passaggio 5](#step-5).

+++

## Passaggio 4 - Risoluzione dei problemi di installazione di /tmp piena {#step-4}

+++**Risolvere i problemi relativi al montaggio /tmp pieno**

[Risolvere i problemi relativi al montaggio /tmp pieno per Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md), scorri l’articolo verso il basso e prova le soluzioni e le best practice. Quindi esegui `df -h | grep mysql` e poi `df -h | grep tmp` nella CLI/Terminal per verificare l&#39;utilizzo dello spazio su disco in `/tmp` e `/data/mysql` directory\
  &lt; 70% utilizzato?

>[!NOTE]
>
>Le soluzioni in [Risolvere i problemi relativi al montaggio /tmp pieno per Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md) sono progettate per i commercianti che non hanno modificato le variabili per il timdir del database, che per impostazione predefinita scrive in `/tmp`. Se è stato modificato il valore tmpdir, le istruzioni in [Risolvere i problemi relativi al montaggio /tmp pieno per Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md) non aiuterà.

a. SÌ - Il problema è stato risolto. \
b. N. - [Invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), per richiedere più spazio.

+++

## Passaggio 5: selezionare il valore predefinito {#step-5}

+++**Seleziona predefinito**

È possibile che la configurazione del database non sia più impostata sul valore predefinito originale. Trovare la configurazione tmpdir del database eseguendo in MySQL CLI: `SELECT @@DATADIR;`. Se `/data/mysql/` viene generato, il tmpdir del database sta scrivendo in `/data/mysql/`. Prova ad aumentare lo spazio in questa directory seguendo i passaggi descritti in [Lo spazio su disco di MySQL è insufficiente in Adobe Commerce nell’infrastruttura cloud](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md). Quindi esegui `df -h | grep mysql` e poi `df -h | grep tmp` nella CLI/Terminal per verificare l&#39;utilizzo dello spazio su disco in `/data/mysql` e `/tmp`.\
  &lt; 70% utilizzato?

a. SÌ - Il problema è stato risolto. \
b. N. - [Invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), per richiedere più spazio.

+++

[Torna al passaggio 1](#step-1)
