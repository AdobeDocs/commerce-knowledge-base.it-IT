---
title: Risoluzione dei problemi di distribuzione di Adobe Commerce
description: Le distribuzioni bloccate e non riuscite in Adobe Commerce possono essere risolte utilizzando lo strumento di risoluzione dei problemi di distribuzione. Fare clic su ogni domanda per visualizzare la risposta in ogni passaggio della risoluzione dei problemi.
exl-id: 5141e079-be61-44c2-8bff-c4b13cb7e07c
feature: Build, Deploy, Support
role: Developer
source-git-commit: 4704446d043e3175b5af27c068908e58bfb7a9ff
workflow-type: tm+mt
source-wordcount: '959'
ht-degree: 0%

---

# Risoluzione dei problemi di distribuzione di Adobe Commerce

Le distribuzioni bloccate e non riuscite in Adobe Commerce possono essere risolte utilizzando lo strumento di risoluzione dei problemi di distribuzione. Fare clic su ogni domanda per visualizzare la risposta in ogni passaggio della risoluzione dei problemi.

## Passaggio 1: verificare che il servizio sia in esecuzione {#step-1}

+++**Il servizio Adobe Commerce sull&#39;infrastruttura cloud è attivo?**

Distribuzione bloccata: Adobe Commerce su infrastruttura cloud è attivo? Seleziona [Adobe Commerce Cloud](https://status.adobe.com/products/3350/).

a. SÌ - Procedere al [passaggio 2](#step-2).\
b. NO - Manutenzione o interruzioni globali. Controlla la durata stimata e gli aggiornamenti.

+++

## Passaggio 2: controllare le distribuzioni in altri ambienti {#step-2}

+++**Esistono distribuzioni in altri ambienti che bloccano la distribuzione nell&#39;ambiente esistente?**

Per ottenere un elenco delle attività in corso, esegui il seguente comando utilizzando magento-cloud CLI (se sei stato aggiunto a un solo progetto cloud). **Nota**: verifica di essere nella versione più recente di CLI di Magento-Cloud. Per i passaggi, fare riferimento a [Aggiornare CLI](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/cloud-cli/cloud-cli-overview) nella guida Commerce su Cloud Infrastructure.

```bash
magento-cloud --state=in_progress
```

Per ottenere un elenco delle attività in corso, esegui il seguente comando utilizzando Magento-cloud CLI (se sei stato aggiunto a più progetti):

```bash
magento-cloud -p <project-id or project-url> --state=in_progress
```

Per trovare informazioni su un&#39;attività di distribuzione esistente (fare riferimento a [Verifica del registro di distribuzione se l&#39;interfaccia utente di Cloud presenta un errore &quot;log snipped&quot;](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error)
per ulteriori dettagli) puoi eseguire questo comando per ottenere un registro in esecuzione dell’attività:

```bash
magento-cloud activity:log <activity-id> [OPTIONAL: <-p project-id or project-url>]
```

a. YES - Risolvere i problemi relativi all’altro ambiente che blocca la distribuzione nell’ambiente esistente. Procedi al [passaggio 3](#step-3).

b. NO - Risolvere i problemi relativi all’ambiente corrente. Procedi al [passaggio 3](#step-3).

+++


## Passaggio 3: verificare SSH su tutti i nodi {#step-3}

+++**SSH riuscito in tutti i nodi?**

a. SÌ - Procedere al [passaggio 4](#step-4).\
b. NO - [Invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Passaggio 4: verificare tutti i servizi in esecuzione {#step-4}

+++**Tutti i servizi sono in esecuzione?**

a. SÌ - Procedere al [passaggio 5](#step-5).\
b. NO - [Invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Passaggio 5: verificare l’esecuzione del bitbucket {#step-5}

+++**Utilizzo di Bitbucket?**

a. SÌ - Controllare [status.bitbucket.com](https://bitbucket.status.atlassian.com/).\
b. NO - Controllare gli errori del registro di distribuzione nei [registri di compilazione e distribuzione](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/test/log-locations). Procedi al [passaggio 6](#step-6).

+++

## Passaggio 6 - Controllare i codici di errore {#step-6}

+++**Codice di errore segnalato?**

a. SÌ - Procedere al [passaggio 7](#step-7).\
b. NO - Procedi al [passaggio 8](#step-8).

+++

## Passaggio 7 - Errore 403 non consentito {#step-7}

+++**403 Non consentito?**

a. SÌ - Procedere al [passaggio 16](#step-16).
b. NO - Procedi al [passaggio 9](#step-9).

+++

## Passaggio 8: verificare i processi cron in esecuzione {#step-8}

+++**I processi cron sono attualmente in esecuzione?** Accedi da ssh sul ramo ed esegui `ps aufxx |grep cron`.

a. SÌ - Accesso tramite ssh sul ramo interessato (ad esempio primario). Uccidi e sblocca i lavori cron. In questo modo verranno terminati i processi cron e verrà reimpostato lo stato. Eseguire `php vendor/bin/ece-tools cron:kill` e quindi `php vendor/bin/ece-tools cron:unlock`. Se stavi unendo un ambiente in un altro, controlla entrambi gli ambienti per individuare eventuali nodi in esecuzione.\
b. NO - Procedi al [passaggio 17](#step-17).

+++

## Passaggio 9: errore dell&#39;applicazione distribuibile nel cluster remoto {#step-9}

+++**Errore durante il caricamento dell&#39;applicazione nel cluster remoto?**

a. SÌ - Procedere al [passaggio 10](#step-10).\
b. NO - Procedi al [passaggio 11](#step-11).

+++

## Passaggio 10 - Controllare che la memoria sia sufficiente {#step-10}

+++**Spazio di archiviazione disponibile valido?**

a. SÌ - Procedere con [Passaggio 11](#step-11).\
b. NO - Rivedi [Gestione spazio su disco](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/storage/manage-disk-space).

+++

## Passaggio 11 - Verificare lo spazio su disco {#step-11}

+++Impossibile scrivere il file **_Avviso _?**

a. SÌ - [aumenta il valore del disco in .magento.app.yaml](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html#application-disk-space) e ridistribuiscilo. Se non funziona, [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO - Procedere con [Passaggio 12](#step-12).

+++

## Passaggio 12 - Errore di ridistribuzione dell’ambiente non riuscita {#step-12}

+++**Errore di ridistribuzione ambiente non riuscita?**

a. SÌ - Procedere con [Passaggio 13](#step-13).\
b. NO - Procedere con [Passaggio 8](#step-8).

+++

## Passaggio 13: verifica della presenza di errori di aggiornamento Elasticsearch {#step-13}

+++**Aggiornamento o distribuzione di Elasticsearch in corso?**

a. YES - Passaggi di aggiornamento non riusciti in Elasticsearch. Consulta [Compatibilità del software Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html). Se l&#39;aggiornamento di Elasticsearch non funziona ancora, [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket). **Nota**: in Adobe Commerce su infrastruttura cloud, tieni presente che gli aggiornamenti del servizio non possono essere inviati all&#39;ambiente di produzione senza un preavviso di 48 ore lavorative al nostro team di infrastruttura. Ciò è necessario in quanto è necessario disporre di un tecnico di supporto dell&#39;infrastruttura per aggiornare la configurazione entro l&#39;intervallo di tempo desiderato, riducendo al minimo i tempi di inattività dell&#39;ambiente di produzione. Quindi, 48 ore prima del momento in cui le modifiche devono essere in produzione, [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) specificando l&#39;aggiornamento del servizio richiesto e indicando l&#39;ora in cui desideri avviare il processo di aggiornamento.\
b. NO - Procedi al [passaggio 14](#step-14).

+++

## Passaggio 14 - Controllare i limiti di spazio {#step-14}

+++**Il file system è esaurito negli inodi o nello spazio?**

a. SÌ - Vedere [Gestione spazio su disco](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html#application-disk-space).\
b. NO - Procedi al [passaggio 15](#step-15).

+++

## Passaggio 15: errore di versione di Elasticsearch {#step-15}

+++**Errore nelle versioni di Elasticseach?**

a. SÌ - Procedere al [passaggio 16](#step-16).\
b. NO - Procedi al [passaggio 21](#step-21).

+++

## Passaggio 16: verificare la configurazione del Compositore {#step-16}

+++**Configurazione del compositore corretta?**

a. SÌ - Procedere al [passaggio 10](#step-10).\
b. NO - Rivedi [pagina Web Risoluzione problemi compositore](https://getcomposer.org/doc/articles/troubleshooting.md).

+++

## Passaggio 17: verificare la presenza di processi con tempi di esecuzione lunghi {#step-17}

+++**Processi con esecuzione prolungata?**

a. SÌ - Identificare i processi a esecuzione prolungata e quindi terminare i processi:
1. Eseguire il comando seguente nel terminale: `ps aufx`.
1. Individuare il PID del processo a esecuzione prolungata.
1. Terminare il processo utilizzando `kill -9 <PID>`.

Monitora le distribuzioni per verificare la ricorrenza.

b. NO - Procedi al [passaggio 18](#step-18).

+++

## Passaggio 18 - Controllare la presenza di eventuali guasti al gancio posteriore {#step-18}

+++**Errore/blocco post hook?**

a. SÌ - Database: [Spazio libero su disco](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html#allocate-disk-space), tabelle danneggiate o incomplete.\
b. NO - Procedi al [passaggio 19](#step-19).

+++

## Passaggio 19: verificare se le estensioni di terze parti bloccano la distribuzione {#step-19}

+++**Utilizzo di estensioni di terze parti?**

a. SÌ - Provare a [Disabilitare le estensioni di terze parti](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure-store/extensions) ed eseguire la distribuzione (per verificare se sono la causa del problema), soprattutto se sono presenti nomi di estensione in errori.\
b. NO - Procedi al [passaggio 20](#step-20).

+++

## Passaggio 20: verificare la presenza di query lente {#step-20}

+++**Query con esecuzione prolungata?**

[Controllare il log delle query lente e MySQL show processlist](/help/troubleshooting/database/checking-slow-queries-and-processes-mysql.md).

a. YES - Elimina le query con tempi di esecuzione lunghi. Rivedi [Sintassi di terminazione MySQL.](https://dev.mysql.com/doc/refman/8.0/en/kill.html)\
b. NO - [Invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Passaggio 21 - Downgrade della versione di Elasticsearch {#step-21}

+++**Eseguire il downgrade delle versioni di Elasticsearch?**

a. SÌ - Non è possibile eseguire la configurazione. [Invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO - [Invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

[Torna al passaggio 1](#step-1)
