---
title: "[!DNL Cron] processo bloccato nello stato **in esecuzione**"
description: Questo articolo fornisce soluzioni per quando Adobe Commerce [!DNL cron] i processi non vengono completati e persistono in uno stato "in esecuzione", che impedisce ad altri [!DNL cron] processi dall'esecuzione. Ciò può verificarsi per diversi motivi, ad esempio problemi di rete, arresti anomali dell’applicazione e problemi di ridistribuzione.
exl-id: 11e01a2b-2fcf-48c2-871c-08f29cd76250
feature: Configuration
role: Developer
source-git-commit: 08a241131453725a86eda5f267a209e6705da2e3
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# [!DNL Cron] il processo è bloccato nello stato &quot;in esecuzione&quot;

Questo articolo fornisce soluzioni per quando Adobe Commerce [!DNL cron] i processi non vengono completati e persistono in uno stato &quot;in esecuzione&quot;, che impedisce ad altri [!DNL cron] processi dall&#39;esecuzione. Ciò può verificarsi per diversi motivi, ad esempio problemi di rete, arresti anomali dell’applicazione e problemi di ridistribuzione.

## Prodotti e versioni interessati

Adobe Commerce su infrastruttura cloud, tutte le versioni

## Sintomo {#symptom}

Sintomi di [!DNL cron] i processi che devono essere reimpostati includono:

* Nella finestra è visualizzata una grande quantità di OdL `cron_schedule` coda
* Le prestazioni del sito iniziano a peggiorare
* I processi non vengono eseguiti secondo la pianificazione

## Soluzioni {#solutions}

### Soluzione per arrestare tutti [!DNL cron] processi contemporaneamente {#solution-stop-all-crons-at-once}

>[!WARNING]
>
>Esecuzione del comando senza `--job-code` ripristini opzioni *tutto* [!DNL cron] processi, inclusi quelli attualmente in esecuzione, pertanto si consiglia di utilizzarlo solo in casi eccezionali, ad esempio dopo aver verificato che tutti [!DNL cron] i processi devono essere reimpostati. La ridistribuzione esegue questo comando per impostazione predefinita per reimpostare [!DNL cron] in modo da ripristinarli in modo appropriato dopo il backup dell&#39;ambiente. Evita di utilizzare questa soluzione quando gli indicizzatori sono in esecuzione.

Per risolvere questo problema, è necessario reimpostare il [!DNL cron] processo/i che utilizzano `cron:unlock` comando. Questo comando modifica lo stato del [!DNL cron] nel database, terminando il processo forzatamente per consentire la continuazione di altri processi pianificati.

1. Aprire un terminale e utilizzare [Chiavi SSH](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections) per connettersi all&#39;ambiente interessato.
1. Ottenere le credenziali del database MySQL:    ```shell    echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp    ```
1. Connettersi al database utilizzando `mysql` :    ```shell    mysql -hdatabase.internal -uuser -ppassword main    ```
1. Seleziona la `main` database:    ```shell    use main    ```
1. Trova tutte le in esecuzione [!DNL cron] processi:    ```shell    SELECT * FROM cron_schedule WHERE status = 'running';    ```
1. Copia il `job_code` di qualsiasi processo in esecuzione per un periodo più lungo del solito.
1. Utilizza gli ID pianificazione del passaggio precedente per sbloccare specifici [!DNL cron] processi:    ```shell    ./vendor/bin/ece-tools cron:unlock --job-code=<job_code_1> [... --job-code=<job_code_x>]    ```

### Soluzione per arrestare un singolo [!DNL cron] {#solution-stop-a-single-cron}

1. Aprire un terminale e utilizzare [Chiavi SSH](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections) per connettersi all&#39;ambiente interessato.
1. Controllare le attività con tempi di esecuzione lunghi utilizzando il comando seguente:

   ```date; ps aux | grep '[%]CPU\|cron\|magento\|queue' | grep -v 'grep\|cron -f'```

1. Nell’output, come nell’output di esempio riportato di seguito, verranno visualizzate la data corrente e l’elenco dei processi. Il `START` la colonna mostra l&#39;ora di inizio o la data del processo:

   ```
   Wed May  8 22:41:31 UTC 2019
   USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
   root       590  0.0  0.0  27528  2768 ?        Ss   Jan15   0:49 /usr/sbin/cron -f
   bxc2qly+ 25855  0.0  0.0  23724  2184 ?        S    20:51   0:00 logger -d -u /run/bxc2qlykqhbqe_stg-cron.sock -p cron.info -s -t cron-bxc2qlykqhbqe_stg-bxc2qlykqhbqe_stg
   bxc2qly+ 25860 57.7  1.3 584220 222692 ?       S    20:51   0:02 php bin/magento cron:run
   bxc2qly+ 25863  0.0  0.0  23724  2472 ?        S    20:51   0:00 logger -d -u /run/bxc2qlykqhbqe-cron.sock -p cron.info -s -t cron-bxc2qlykqhbqe-bxc2qlykqhbqe
   bxc2qly+ 25876 53.0  0.6 475472 111468 ?       R    20:51   0:01 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25878 57.0  0.6 475472 112080 ?       R    20:51   0:01 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=staging --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25880 50.5  0.6 475472 111312 ?       R    20:51   0:01 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=catalog_event --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25882 48.5  0.6 475472 111220 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=consumers --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25884 50.5  0.6 475472 111372 ?       R    20:51   0:01 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=ddg_automation --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25890 32.5  0.6 475368 110672 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe/bin/magento cron:run --group=staging --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25892 34.5  0.6 475472 110724 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe/bin/magento cron:run --group=catalog_event --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25894 31.5  0.6 475368 110136 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe/bin/magento cron:run --group=consumers --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25896 29.0  0.6 475320 109876 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe/bin/magento cron:run --group=ddg_automation --bootstrap=standaloneProcessStarted=1
   ```

1. Se si verifica un problema di lunga durata [!DNL cron] processi che possono costituire il processo di distribuzione del blocco, è possibile terminare il processo utilizzando `kill` comando. È possibile identificare **ID processo** (trovato il `PID` ), quindi inseriscilo `PID` nel comando per terminare il processo.
Il **termina processo** il comando è:

   ```kill -9 <PID>```

1. Puoi quindi distribuirla nuovamente, se stavi tentando di distribuirla nuovamente.
