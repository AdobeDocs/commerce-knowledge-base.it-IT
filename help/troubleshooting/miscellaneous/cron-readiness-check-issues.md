---
title: Problemi relativi al controllo di preparazione al problema
description: '"Questo articolo fornisce soluzioni per i problemi di preparazione alla cron. I seguenti sono sintomi di problemi di cron:'''
exl-id: 1f2cee2c-98ad-4cf5-af16-d736fced2a15
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# Problemi relativi al controllo di preparazione al problema

Questo articolo fornisce soluzioni per i problemi di preparazione alla cron. Di seguito sono riportati i sintomi di problemi di cron:

* Messaggio di errore sull&#39;impostazione PHP `$HTTP_RAW_POST_DATA` viene visualizzato anche se è impostato correttamente.
* Il controllo di preparazione PHP non visualizza la versione PHP, come illustrato nella figura riportata di seguito.
  ![upgr-tshoot-no-cron.png](assets/upgr-tshoot-no-cron.png)
* In Commerce Admin viene visualizzato il seguente errore:
  ![compman-cron-not-running.png](assets/compman-cron-not-running.png)
Per visualizzare l’errore, potrebbe essere necessario fare clic su **Messaggi di sistema** nella parte superiore della finestra come segue:
  ![compman_sys-messages.png](assets/compman_sys-messages.png)

## Controlla la tua linguetta cronologica esistente {#check-your-existing-crontab}

Questa sezione illustra come verificare se cron è attualmente in esecuzione e se è configurato correttamente.

Per verificare se la scheda cronologica è configurata o meno:

1. Accedi al server Commerce come, o passa a [proprietario file system di Magento](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/file-sys-perms-over.html).
1. Verifica se esiste il seguente file: `$ ls -al <magento_root>/var/.setup_cronjob_status`. Se il file esiste, cron è stato eseguito correttamente in passato. Se il file *non* esiste, Adobe Commerce non è ancora stato installato oppure cron non è in esecuzione. In entrambi i casi, continuare con il passaggio successivo.
1. Maggiori dettagli su cron. Come utente con `root` , immetti il seguente comando: `$ crontab -u <Magento file system owner name> -l`. Ad esempio, su CentOS `$ crontab -u magento_user -l`. Se non è stata impostata alcuna scheda cronologica per l’utente, viene visualizzato il seguente messaggio:    `no crontab for magento_user`. La scheda cronologica indica quanto segue:
   * Che tipo di file binario PHP si sta utilizzando (in alcuni casi ne è presente più di uno)
   * Quali script cron di Adobe Commerce stai eseguendo (in particolare, i percorsi di tali script)
   * Dove si trovano i registri cron

   Consulta una delle seguenti sezioni per una soluzione al problema.

## Soluzione: clienttab non configurato {#solution-crontab-not-set-up}

Per verificare che i processi cron siano configurati correttamente, consulta [Imposta processi cron](https://devdocs.magento.com/guides/v2.3/install-gde/install/post-install-config.html#post-install-cron) nella documentazione per gli sviluppatori.

## Soluzione: cron in esecuzione da un file binario PHP non corretto {#solution-cron-running-from-incorrect-php-binary}

Se il processo cron utilizza un file binario PHP diverso dal plug-in del server Web, potrebbero essere visualizzati errori di impostazioni PHP. Per risolvere il problema, impostare impostazioni PHP identiche sia per la riga di comando PHP che per il plug-in del server Web PHP.

Per ulteriori informazioni sulle impostazioni PHP, vedere [Impostazioni PHP richieste](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html) nella documentazione per gli sviluppatori.

## Soluzione: cron in esecuzione con errori {#solution-cron-running-with-errors}

Provare a eseguire ogni comando manualmente perché il comando potrebbe visualizzare utili messaggi di errore. Consulta [Imposta processi cron](https://devdocs.magento.com/guides/v2.3/install-gde/install/post-install-config.html#post-install-cron) nella documentazione per gli sviluppatori.

>[!NOTE]
>
>Esegui almeno cron *due volte* per l&#39;esecuzione del job; la prima volta per mettere in coda i job, la seconda volta per eseguire i job.
