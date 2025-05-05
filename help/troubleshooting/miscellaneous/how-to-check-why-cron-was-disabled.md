---
title: Verificare il motivo della disabilitazione di  [!DNL cron]
description: Questo articolo offre soluzioni per la risoluzione dei problemi relativi ai cron in Adobe Commerce sui prodotti dell’infrastruttura cloud.
feature: Configuration
role: Developer
exl-id: d4d4a28d-3afa-4379-afc1-bc6250717784
source-git-commit: c5e94c6407394cd905ea470628d28db2c2c6c0ed
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# Verificare il motivo per cui [!DNL cron] è stato disabilitato

Questo articolo offre soluzioni per la risoluzione dei problemi relativi a [!DNL cron] nei prodotti Adobe Commerce per infrastrutture cloud.

## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud, tutte le versioni

## Problema

## Di seguito sono riportati i sintomi di [!DNL cron] problemi:

Hai notato che [!DNL cron] non era in esecuzione.
Ad esempio: vengono visualizzate le righe seguenti nel file `app/etc/env.php`:

```'cron' =>
  array (
    'enabled' => 0
  ),
```

Un array vuoto indica che [!DNL cron] è **abilitato**:

```'cron' =>
  array (
  ),
```

## Cause

Ci sono diversi motivi per cui [!DNL cron] non è attualmente attivo:

1. [!DNL cron] è stato disabilitato a causa di [!DNL OpCache] impostazioni mancanti.
1. Il team dell&#39;infrastruttura ha disabilitato [!DNL cron] perché causava un calo delle prestazioni del sito.
1. [!DNL cron] non è stato riabilitato perché la distribuzione non è riuscita.

Consulta una delle seguenti sezioni per una soluzione al problema.

## Soluzioni

### Soluzione per le impostazioni [!DNL OpCache] mancanti {#solution-missed-opcache-settings}

Vedi [[!DNL Cron] arrestato a causa di configurazione errata o impostazioni mancanti [!DNL OpCache] nella Knowledge Base di Commerce](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/crons-blocked-running-missing-opache-settings).

### Soluzione per utenti disabili dal team di infrastruttura {#solution-disabled-by-infrastructure-team}

1. Controlla i ticket di supporto precedenti in cui il tuo sito non rispondeva o non rispondeva.
1. Verificare quindi se il team Infrastruttura ha segnalato di averlo disabilitato.
1. Verificare di aver risolto i problemi segnalati dal team Infrastruttura.
1. Inviare una [richiesta di supporto](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-tickets) se è necessaria ulteriore assistenza per richiedere la riattivazione di [!DNL cron] e spiegare come sono stati risolti i problemi indicati dal team Infrastruttura.

### Impossibile distribuire la soluzione {#solution-deployment-failed}

Controlla i registri di distribuzione:

* [Visualizza e gestisci i registri](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/test/log-locations) nella Guida all&#39;infrastruttura di Commerce su Cloud.
* [Verifica del registro di distribuzione se nell&#39;interfaccia utente di Cloud è presente *`log snipped`* errore](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error) nella Knowledge Base di Commerce.

1. Se la distribuzione non è riuscita durante il passaggio `setup:upgrade`, [!DNL cron] non sarà stato riabilitato.
Ad esempio: vedi questa riga nel registro di distribuzione:

   ```The command "/bin/bash -c "set -o pipefail; php ./bin/magento setup:upgrade --keep-generated --ansi --no-interaction  | tee -a /app/$<project_id>/var/log/install_upgrade.log"" failed. Cache types config flushed successfully```

1. In caso contrario, la distribuzione potrebbe non essere riuscita durante un’altra fase. Controlla il registro di distribuzione e accertati che entrambe le righe siano visualizzate (esempio di seguito). Se nel registro non vengono visualizzate entrambe le righe simili, significa che [!DNL cron] non è stato riabilitato:

   ```  [2024-03-06T10:55:39.345564+00:00] INFO: Disable cron```<br>
...<br>
   ```  [2024-02-07T10:50:09.579005+00:00] INFO: Enable cron```

**Invia una [richiesta di supporto](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-tickets) se hai bisogno di ulteriore assistenza.**
