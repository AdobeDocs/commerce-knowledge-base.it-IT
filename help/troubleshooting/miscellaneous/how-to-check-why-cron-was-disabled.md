---
title: Come verificare il motivo [!DNL cron] è stato disabilitato
description: Questo articolo offre soluzioni per la risoluzione dei problemi relativi ai cron in Adobe Commerce sui prodotti dell’infrastruttura cloud.
feature: Configuration
role: Developer
exl-id: d4d4a28d-3afa-4379-afc1-bc6250717784
source-git-commit: c5e94c6407394cd905ea470628d28db2c2c6c0ed
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# Come verificare il motivo [!DNL cron] è stato disabilitato

Questo articolo offre soluzioni per la risoluzione dei problemi relativi a [!DNL cron] in Adobe Commerce sui prodotti dell’infrastruttura cloud.

## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud, tutte le versioni

## Problema

## Di seguito sono riportati i sintomi [!DNL cron] problemi:

Hai notato che il tuo [!DNL cron] non stava correndo.
Ad esempio: nelle `app/etc/env.php` file:

```'cron' =>
  array (
    'enabled' => 0
  ),
```

Un array vuoto indica che il [!DNL cron] è **abilitato**:

```'cron' =>
  array (
  ),
```

## Cause

Ci sono diversi motivi per cui [!DNL cron] non è attualmente attivo:

1. Il [!DNL cron] è stato disabilitato a causa di errori [!DNL OpCache] impostazioni.
1. Il team Infrastruttura ha disabilitato [!DNL cron], perché causava un peggioramento delle prestazioni del sito o un peggioramento delle prestazioni.
1. Il [!DNL cron] non è stato riattivato perché la distribuzione non è riuscita.

Consulta una delle seguenti sezioni per una soluzione al problema.

## Soluzioni

### Soluzione per la perdita dei dati [!DNL OpCache] impostazioni {#solution-missed-opcache-settings}

Consulta [[!DNL Cron] interrotto a causa di configurazione errata o mancante [!DNL OpCache] impostazioni](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/crons-blocked-running-missing-opache-settings) nella knowledge base di Commerce.

### Soluzione per utenti disabili dal team di infrastruttura {#solution-disabled-by-infrastructure-team}

1. Controlla i ticket di supporto precedenti in cui il tuo sito non rispondeva o non rispondeva.
1. Verificare quindi se il team Infrastruttura ha segnalato di averlo disabilitato.
1. Verificare di aver risolto i problemi segnalati dal team Infrastruttura.
1. Invia un [Richiesta di supporto](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-tickets) se hai bisogno di ulteriore assistenza per richiedere di riabilitare [!DNL cron] e spiegare come sono stati risolti i problemi indicati dal team Infrastruttura.

### Impossibile distribuire la soluzione {#solution-deployment-failed}

Controlla i registri di distribuzione:

* [Visualizzare e gestire i registri](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations) nella Guida all’infrastruttura Commerce on Cloud.
* [Verifica del registro di distribuzione se l’interfaccia utente cloud dispone di *`log snipped`* errore](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error) nella knowledge base di Commerce.

1. Se la distribuzione non era riuscita durante il `setup:upgrade` passaggio, il [!DNL cron] non sarà stato riattivato.
Ad esempio: vedi questa riga nel registro di distribuzione:

   ```The command "/bin/bash -c "set -o pipefail; php ./bin/magento setup:upgrade --keep-generated --ansi --no-interaction  | tee -a /app/$<project_id>/var/log/install_upgrade.log"" failed. Cache types config flushed successfully```

1. In caso contrario, la distribuzione potrebbe non essere riuscita durante un’altra fase. Controlla il registro di distribuzione e accertati che entrambe le righe siano visualizzate (esempio di seguito). Se non trovi entrambe le righe simili nel registro, significa che il [!DNL cron] non è stato riabilitato:

   ```  [2024-03-06T10:55:39.345564+00:00] INFO: Disable cron```<br>
...<br>
   ```  [2024-02-07T10:50:09.579005+00:00] INFO: Enable cron```

**Invia un [Richiesta di supporto](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-tickets) se ha bisogno di ulteriore assistenza.**
