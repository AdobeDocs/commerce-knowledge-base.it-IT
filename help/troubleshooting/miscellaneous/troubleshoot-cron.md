---
title: Risolvere i problemi relativi a cron
description: Questo articolo offre soluzioni per la risoluzione dei problemi relativi ai cron nei prodotti Adobe Commerce on-premise.
exl-id: e69a4fb3-731b-449e-a815-c33cd2faa567
feature: Configuration
role: Developer
source-git-commit: b6a79bcff3d757d40e7070182d8853a37960a782
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# Risolvere i problemi relativi a cron

Questo articolo offre soluzioni per la risoluzione dei problemi relativi ai cron nei prodotti Adobe Commerce on-premise.

## Prodotti e versioni interessati

* Adobe Commerce on-premise 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x

## Problemi

## Di seguito sono riportati i sintomi di problemi di cron:

* L&#39;aggiornamento o l&#39;aggiornamento non viene mai eseguito. Rimane nello stato `pending`.
* Viene visualizzato un messaggio di errore sull&#39;impostazione `$HTTP_RAW_POST_DATA` di [PHP](https://glossary.magento.com/php) anche se è impostata correttamente.
* Il controllo di preparazione al cron non riesce. I possibili errori includono percorsi non scrivibili e cron non impostato. Di seguito è riportato un esempio:

  ![upgr-tshoot-no-cron2.png](assets/upgr-tshoot-no-cron2.png)

* Il controllo di preparazione PHP non visualizza la versione PHP, come illustrato nella figura riportata di seguito.

  ![Screen_Shot_2019-08-29_at_1.36.08_PM.png](assets/Screen_Shot_2019-08-29_at_1.36.08_PM.png)

* In Commerce Admin viene visualizzato il seguente errore:

  ![compman-cron-not-running.png](assets/compman-cron-not-running.png)

Per visualizzare l&#39;errore, potrebbe essere necessario fare clic su **Messaggi di sistema** nella parte superiore della finestra nel modo seguente:

![compman_sys-messages.png](assets/compman_sys-messages.png)

## Ricercare la causa {#check-your-existing-crontab}

Questa sezione illustra come verificare se cron è attualmente in esecuzione e se è configurato correttamente.

Per verificare se la scheda cronologica è configurata o meno, effettuare le seguenti operazioni:

1. Accedi al server di Magento come [proprietario del file system di Magento](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/file-sys-perms-over.html) o passa a tale proprietario.
1. Verifica se esiste il seguente file:    `bash    ls -al <magento_root>/var/.setup_cronjob_status`. Se il file esiste, cron è stato eseguito correttamente in passato. Se il file *non esiste*, il Magento non è ancora stato installato oppure cron non è in esecuzione. In entrambi i casi, continuare con il passaggio successivo.
1. Maggiori dettagli su cron. In qualità di utente con privilegi `root`, immetti il comando seguente:    `bash    crontab -u <Magento file system owner name> -l`. Ad esempio, su CentOS `bash    crontab -u magento_user -l`.  Se non è stata impostata alcuna scheda cronologica per l’utente, viene visualizzato il seguente messaggio:    `terminal    no crontab for magento_user`. La scheda cronologica indica quanto segue:

   * Che tipo di file binario PHP si sta utilizzando (in alcuni casi ne è presente più di uno)
   * Il Magento degli script cron in esecuzione, in particolare i percorsi di tali script
   * Dove si trovano i registri cron

Consulta una delle seguenti sezioni per una soluzione al problema.

## Soluzioni

### Configurazione della soluzione per crontab non in corso {#solution-crontab-not-set-up}

Per verificare che i processi cron siano configurati correttamente, vedi [Configurazione dei processi cron](https://devdocs.magento.com/guides/v2.3/install-gde/install/post-install-config.html#post-install-cron).

### Soluzione per cron in esecuzione da un binario PHP errato {#solution-cron-running-from-incorrect-php-binary}

Se il processo cron utilizza un file binario PHP diverso dal plug-in del server Web, potrebbero essere visualizzati errori di impostazioni PHP. Per risolvere il problema, impostare impostazioni PHP identiche sia per la riga di comando PHP che per il plug-in del server Web PHP.

Per ulteriori informazioni sulle impostazioni PHP, vedere [Impostazioni PHP richieste](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html) nella documentazione per gli sviluppatori.

### Soluzione per cron in esecuzione con errori {#solution-cron-running-with-errors}

Provare a eseguire ogni comando manualmente perché il comando potrebbe visualizzare utili messaggi di errore. Consulta [Configurare i processi cron](https://devdocs.magento.com/guides/v2.3/install-gde/install/post-install-config.html#post-install-cron).

>[!NOTE]
>
>È necessario eseguire cron almeno *due volte* affinché il processo venga eseguito; la prima volta per mettere in coda i processi, la seconda volta per eseguire i processi.
