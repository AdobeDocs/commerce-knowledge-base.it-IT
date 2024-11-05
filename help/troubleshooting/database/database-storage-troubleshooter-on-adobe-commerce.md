---
title: Risoluzione dei problemi di archiviazione del database su Adobe Commerce
description: Questo articolo è uno strumento di risoluzione dei problemi per i clienti che su Adobe Commerce hanno problemi con i database. Fare clic su ogni domanda per visualizzare la risposta in ogni passaggio della risoluzione dei problemi. A seconda dei sintomi e della configurazione, lo strumento di risoluzione dei problemi spiegherà come risolvere i problemi di spazio e configurazione con i database.
exl-id: f7b09023-7129-4fd0-9bb5-02a2228bc148
feature: Observability, Services, Storage, Support
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 0%

---

# Risoluzione dei problemi di archiviazione del database su Adobe Commerce

Questo articolo è uno strumento di risoluzione dei problemi per i clienti che su Adobe Commerce hanno problemi con i database. Fare clic su ogni domanda per visualizzare la risposta in ogni passaggio della risoluzione dei problemi. A seconda dei sintomi e della configurazione, lo strumento di risoluzione dei problemi spiegherà come risolvere i problemi di spazio e configurazione con i database.

## Passaggio 1: identificazione della directory con un problema di spazio {#step-1}

+++**Si è verificato un problema di `/tmp` causato dalla mancanza di spazio?**

Ciò può essere indicato da una serie di sintomi, tra cui il montaggio `/tmp` pieno, il sito inattivo o l&#39;impossibilità di SSH in un nodo. Potresti anche riscontrare errori come _Spazio esaurito sul dispositivo (28)_. Per un elenco degli errori risultanti dal completamento di `/tmp`, esaminare [/tmp mount full](/help/troubleshooting/miscellaneous/tmp-mount-full.md).

Oppure si è verificato un problema di `/data/mysql` causato dalla mancanza di spazio? Ciò può essere indicato anche da una serie di sintomi, tra cui l&#39;interruzione del sito, l&#39;impossibilità per i clienti di aggiungere prodotti al carrello, l&#39;errore di connessione al database e gli errori di Galeria come _SQLSTATE\[08S01\]: errore del collegamento di comunicazione: 1047 WSREP_. Per un elenco degli errori derivanti da uno spazio su disco insufficiente di [!DNL MySQL], vedere [[!DNL MySQL] lo spazio su disco è insufficiente in Adobe Commerce nell&#39;infrastruttura cloud](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md).

Se non si è sicuri di avere un problema di spazio su disco e si dispone di un account New Relic, passare alla [pagina Host di monitoraggio infrastruttura New Relic](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/). A questo punto, fare clic sulla scheda **Archiviazione**, modificare l&#39;elenco a discesa **Grafico mostra** da 5 a 20 risultati ed esaminare la tabella per l&#39;utilizzo su disco elevato nel grafico o nella tabella % utilizzata su disco. Per i passaggi più dettagliati, fare riferimento alla [scheda Monitoraggio infrastruttura New Relic > Archiviazione]https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#storage).

Se si verifica uno dei sintomi descritti in precedenza, controllare lo stato degli inodi per assicurarsi che non sia causato da un problema relativo al numero di file. A tale scopo, eseguire il comando seguente in CLI/Terminal:\
`df -ih`

L’IUse% è > 90%?

a. SÌ - La causa è un numero eccessivo di file. Rivedi i passaggi per rimuovere i file in modo sicuro in [Eliminare i file in modo sicuro quando lo spazio su disco è esaurito, Adobe Commerce sull&#39;infrastruttura cloud](/help/troubleshooting/miscellaneous/safely-delete-files-when-out-of-disk-space-adobe-commerce-on-our-cloud-architecture.md). Procedi al [passaggio 2](#step-2) dopo aver completato questi passaggi. Per richiedere più spazio, [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO - Controllare lo spazio. Eseguire `df -h | grep mysql` e quindi `df -h | grep tmp` nella CLI/Terminal per verificare l&#39;utilizzo dello spazio su disco nelle directory `/tmp` e `/data/mysql`. Procedi al [passaggio 3](#step-3).

+++

## Passaggio 2 - Controllare lo spazio su disco {#step-2}

+++**Controllare l&#39;utilizzo dello spazio su disco?**

Dopo aver ridotto il numero di file, eseguire `df -h | grep mysql` e quindi `df -h | grep tmp` in CLI/Terminal per verificare l&#39;utilizzo dello spazio su disco in `/tmp` e `/data/mysql`. Viene utilizzato più del 70% per `/tmp` o `/data/mysql`?

a. SÌ - Procedere al [passaggio 3](#step-3).
b. NO - È possibile che le query stiano esaurendo lo spazio di archiviazione disponibile. Il nodo potrebbe subire un arresto anomalo, causando l&#39;interruzione della query e la rimozione dei file `tmp`. Esaminare l&#39;output di `SHOW PROCESSLIST;` nella CLI di [!DNL MySQL] per individuare le query che potrebbero essere la causa del problema. [Invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), richiedendo più spazio.

+++

## Passaggio 3: identificazione della directory con utilizzo elevato {#step-3}

+++**Quale directory ha utilizzato più del 70%?**

Quale directory è utilizzata per più del 70%? `/tmp` o `/data/mysql`?

>[!NOTE]
>
>Per impostazione predefinita, tmpdir del database scrive in `/tmp`. Per verificare che la configurazione del database sia ancora impostata su questo valore predefinito, eseguire il comando seguente in [!DNL MySQL] CLI: `SHOW VARIABLES LIKE "TMPDIR";` Se il tmpdir del database scrive ancora in `/tmp`, nella colonna Valore verrà visualizzato `/tmp`.

a. `/tmp` - Procedere al [Passaggio 4](#step-4). \
b. `/data/mysql` - Procedere al [Passaggio 5](#step-5).

+++

## Passaggio 4 - Risoluzione dei problemi di installazione di /tmp piena {#step-4}

+++**Risoluzione dei problemi /tmp mount full**

[Risolvere i problemi relativi al montaggio /tmp completo per Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md), scorrere l&#39;articolo verso il basso e provare le soluzioni e le best practice. Eseguire quindi `df -h | grep mysql` e `df -h | grep tmp` in CLI/Terminal per verificare l&#39;utilizzo dello spazio su disco nelle directory `/tmp` e `/data/mysql`\
  &lt; 70% utilizzato?

>[!NOTE]
>
>Le soluzioni in [Risoluzione dei problemi /tmp mount completo per Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md) sono progettate per i commercianti che non hanno modificato le variabili per il database tmpdir, che per impostazione predefinita scrive in `/tmp`. Se il valore tmpdir è stato modificato, le istruzioni in [Risoluzione dei problemi /tmp mount completo per Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md) non saranno utili.

a. SÌ - Il problema è stato risolto. \
b. NO - [Invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), richiedendo più spazio.

+++

## Passaggio 5: selezionare il valore predefinito {#step-5}

+++**Controlla valore predefinito**

È possibile che la configurazione del database non sia più impostata sul valore predefinito originale. Trovare la configurazione tmpdir del database eseguendo in [!DNL MySQL] CLI: `SELECT @@DATADIR;`. Se viene eseguito l&#39;output di `/data/mysql/`, il tmpdir del database sta scrivendo in `/data/mysql/`. Prova ad aumentare lo spazio in questa directory seguendo la procedura descritta in [[!DNL MySQL] lo spazio su disco in Adobe Commerce è insufficiente nella nostra infrastruttura cloud](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md). Eseguire quindi `df -h | grep mysql` e `df -h | grep tmp` nell&#39;interfaccia CLI/Terminal per verificare l&#39;utilizzo dello spazio su disco in `/data/mysql` e `/tmp`.\
  &lt; 70% utilizzato?

a. SÌ - Il problema è stato risolto. \
b. NO - [Invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), richiedendo più spazio.

+++

[Torna al passaggio 1](#step-1)

## Lettura correlata

* [Best practice per la modifica delle tabelle del database](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) nel playbook di implementazione di Commerce
