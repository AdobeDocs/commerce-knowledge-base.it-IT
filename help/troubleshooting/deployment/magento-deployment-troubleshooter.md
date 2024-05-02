---
title: Risoluzione dei problemi di distribuzione di Adobe Commerce
description: Le distribuzioni bloccate e non riuscite in Adobe Commerce possono essere risolte utilizzando lo strumento di risoluzione dei problemi di distribuzione. Fare clic su ogni domanda per visualizzare la risposta in ogni passaggio della risoluzione dei problemi.
exl-id: 5141e079-be61-44c2-8bff-c4b13cb7e07c
feature: Build, Deploy, Support
role: Developer
source-git-commit: 6177863da268f43cc30119cef6f718a04c46b3e6
workflow-type: tm+mt
source-wordcount: '933'
ht-degree: 0%

---

# Risoluzione dei problemi di distribuzione di Adobe Commerce

Le distribuzioni bloccate e non riuscite in Adobe Commerce possono essere risolte utilizzando lo strumento di risoluzione dei problemi di distribuzione. Fare clic su ogni domanda per visualizzare la risposta in ogni passaggio della risoluzione dei problemi.

## Passaggio 1: verificare che il servizio sia in esecuzione {#step-1}

+++**Adobe Commerce su Cloud Infrastructure Service è attivo?**

Distribuzione bloccata: Adobe Commerce su infrastruttura cloud è attivo? Verifica [Adobe Commerce Cloud](https://status.adobe.com/products/3350/).

a. SÌ - Procedere come segue [Passaggio 2](#step-2).\
b. NO - Manutenzione o interruzioni globali. Controlla la durata stimata e gli aggiornamenti.

+++

## Passaggio 2: controllare le distribuzioni in altri ambienti {#step-2}

+++**Esistono distribuzioni in altri ambienti che bloccano la distribuzione nell’ambiente esistente?**

Per ottenere un elenco delle attività in corso, esegui il seguente comando utilizzando magento-cloud CLI (se sei stato aggiunto a un solo progetto cloud):

```bash
magento-cloud --state=in_progress
```

Per ottenere un elenco delle attività in corso, esegui il seguente comando utilizzando Magento-cloud CLI (se sei stato aggiunto a più progetti):

```bash
magento-cloud -p <project-id or project-url> --state=in_progress
```

Per trovare informazioni su un’attività di distribuzione esistente (consulta [Verifica del registro di distribuzione se nell’interfaccia utente di Cloud è presente l’errore &quot;log snipped&quot;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error.html)
per ulteriori dettagli) puoi eseguire questo comando per ottenere un registro in esecuzione dell’attività:

```bash
magento-cloud activity:log <activity-id> [OPTIONAL: <-p project-id or project-url>]
```

a. YES - Risolvere i problemi relativi all’altro ambiente che blocca la distribuzione nell’ambiente esistente. Procedi a [Passaggio 3](#step-3).

b. NO - Risolvere i problemi relativi all’ambiente corrente. Procedi a [Passaggio 3](#step-3).

+++


## Passaggio 3: verificare SSH su tutti i nodi {#step-3}

+++**SSH riuscito in tutti i nodi?**

a. SÌ - Procedere come segue [Passaggio 4](#step-4).\
b. N. - [Invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Passaggio 4: verificare tutti i servizi in esecuzione {#step-4}

+++**Tutti i servizi sono in esecuzione?**

a. SÌ - Procedere come segue [Passaggio 5](#step-5).\
b. N. - [Invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Passaggio 5: verificare l’esecuzione del bitbucket {#step-5}

+++**Utilizzare Bitbucket?**

a. SÌ - Spunta [status.bitbucket.com](https://bitbucket.status.atlassian.com/).\
b. NO - Controllare gli errori del registro di distribuzione in [Creare e distribuire i registri](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html). Procedi a [Passaggio 6](#step-6).

+++

## Passaggio 6 - Controllare i codici di errore {#step-6}

+++**Codice di errore segnalato?**

a. SÌ - Procedere come segue [Passaggio 7](#step-7).\
b. NO - Procedi a [Passaggio 8](#step-8).

+++

## Passaggio 7 - Errore 403 non consentito {#step-7}

+++**403 Non consentito?**

a. SÌ - Procedere come segue [Passaggio 16](#step-16).
b. NO - Procedi a [Passaggio 9](#step-9).

+++

## Passaggio 8: verificare i processi cron in esecuzione {#step-8}

+++**I processi cron sono attualmente in esecuzione?** Accedi tramite ssh sul ramo ed esegui `ps aufxx |grep cron`.

a. SÌ - Accesso tramite ssh sul ramo interessato (ad esempio primario). Uccidi e sblocca i lavori cron. In questo modo verranno terminati i processi cron e verrà reimpostato lo stato. Esegui `php vendor/bin/ece-tools cron:kill` e poi `php vendor/bin/ece-tools cron:unlock`. Se stavi unendo un ambiente in un altro, controlla entrambi gli ambienti per individuare eventuali nodi in esecuzione.\
b. NO - Procedi a [Passaggio 17](#step-17).

+++

## Passaggio 9: errore dell&#39;applicazione distribuibile nel cluster remoto {#step-9}

+++**Errore durante il caricamento dell&#39;applicazione nel cluster remoto?**

a. SÌ - Procedere come segue [Passaggio 10](#step-10).\
b. NO - Procedi a [Passaggio 11](#step-11).

+++

## Passaggio 10 - Controllare che la memoria sia sufficiente {#step-10}

+++**Spazio di archiviazione disponibile.**

a. SÌ - Procedere con [Passaggio 11](#step-11).\
b. NO - Riesame [Gestione dello spazio su disco](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html).

+++

## Passaggio 11 - Verificare lo spazio su disco {#step-11}

+++**_impossibile scrivere il file Avviso _?**

a. SÌ - Si prega di [aumentare il valore del disco in .magento.app.yaml](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html#application-disk-space) e la ridistribuzione. Se questo non funziona, [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO - Procedere con [Passaggio 12](#step-12).

+++

## Passaggio 12 - Errore di ridistribuzione dell’ambiente non riuscita {#step-12}

+++**Errore di ridistribuzione dell’ambiente non riuscita?**

a. SÌ - Procedere con [Passaggio 13](#step-13).\
b. NO - Procedere con [Passaggio 8](#step-8).

+++

## Passaggio 13: verifica della presenza di un errore di aggiornamento dell’Elasticsearch {#step-13}

+++**Elasticsearch in fase di aggiornamento o distribuzione?**

a. YES - Elasticsearch di passaggi di aggiornamento non riusciti. Fai riferimento a [Elasticsearch compatibilità software](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html). Se l’aggiornamento Elasticsearch non funziona ancora, [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket). **Nota**: in Adobe Commerce su infrastruttura cloud, tieni presente che gli aggiornamenti del servizio non possono essere inviati all’ambiente di produzione senza un preavviso di 48 ore lavorative al nostro team di infrastruttura. Ciò è necessario in quanto è necessario disporre di un tecnico di supporto dell&#39;infrastruttura per aggiornare la configurazione entro l&#39;intervallo di tempo desiderato, riducendo al minimo i tempi di inattività dell&#39;ambiente di produzione. Quindi 48 ore prima di quando le modifiche devono essere in produzione, [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) specificare l&#39;aggiornamento del servizio richiesto e indicare l&#39;ora in cui si desidera avviare il processo di aggiornamento.\
b. NO - Procedi a [Passaggio 14](#step-14).

+++

## Passaggio 14 - Controllare i limiti di spazio {#step-14}

+++**Il file system è esaurito negli inodi o nello spazio?**

a. SÌ - Si veda [Gestione dello spazio su disco](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html#application-disk-space).\
b. NO - Procedi a [Passaggio 15](#step-15).

+++

## Passaggio 15: errore di versione di Elasticsearch {#step-15}

+++**Errore nelle versioni di Elasticseach?**

a. SÌ - Procedere come segue [Passaggio 16](#step-16).\
b. NO - Procedi a [Passaggio 21](#step-21).

+++

## Passaggio 16: verificare la configurazione del Compositore {#step-16}

+++**La configurazione del compositore è corretta?**

a. SÌ - Procedere come segue [Passaggio 10](#step-10).\
b. NO - Riesame [Pagina Web Risoluzione problemi compositore](https://getcomposer.org/doc/articles/troubleshooting.md).

+++

## Passaggio 17: verificare la presenza di processi con tempi di esecuzione lunghi {#step-17}

+++**Processi con tempi di esecuzione lunghi?**

a. SÌ - Identificare i processi a esecuzione prolungata e quindi terminare i processi:
1. Esegui il comando seguente nel terminale: `ps aufx`.
1. Individuare il PID del processo a esecuzione prolungata.
1. Termina il processo utilizzando `kill -9 <PID>`.

Monitora le distribuzioni per verificare la ricorrenza.

b. NO - Procedi a [Passaggio 18](#step-18).

+++

## Passaggio 18 - Controllare la presenza di eventuali guasti al gancio posteriore {#step-18}

+++**Errore/blocco post-hook?**

a. SÌ - Banca dati: [Spazio libero su disco](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html#allocate-disk-space), danneggiamento, tabelle incomplete/danneggiate.\
b. NO - Procedi a [Passaggio 19](#step-19).

+++

## Passaggio 19: verificare se le estensioni di terze parti bloccano la distribuzione {#step-19}

+++**Utilizzare estensioni di terze parti?**

a. SÌ - Provare [Disabilitazione delle estensioni di terze parti](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/extensions.html) ed eseguendo la distribuzione (per vedere se sono la causa del problema), soprattutto se sono presenti nomi di estensione in eventuali errori.\
b. NO - Procedi a [Passaggio 20](#step-20).

+++

## Passaggio 20: verificare la presenza di query lente {#step-20}

+++**Query con esecuzione prolungata?**

[Controllare il log delle query lente e l&#39;elenco di processi MySQL](/help/troubleshooting/database/checking-slow-queries-and-processes-mysql.md).

a. YES - Elimina le query con tempi di esecuzione lunghi. Revisione [Sintassi di terminazione MySQL.](https://dev.mysql.com/doc/refman/8.0/en/kill.html)\
b. N. - [Invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Passaggio 21 - Downgrade della versione dell’Elasticsearch {#step-21}

+++**Effettuare il downgrade delle versioni di Elasticsearch?**

a. SÌ - Non è possibile eseguire la configurazione. [Invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. N. - [Invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

[Torna al passaggio 1](#step-1)
