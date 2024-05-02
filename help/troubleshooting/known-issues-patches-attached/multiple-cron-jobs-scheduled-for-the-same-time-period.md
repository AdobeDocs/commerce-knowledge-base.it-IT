---
title: Più processi cron pianificati per lo stesso periodo di tempo
description: Questo articolo fornisce una patch per un problema noto di Adobe Commerce 2.2.2 relativo alla pianificazione di più processi cron contemporaneamente dopo la modifica delle variabili di tempo per alcune attività in Commerce Admin.
exl-id: a3c1fe77-ed4c-43b5-8d6f-e5c549096c73
feature: Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '734'
ht-degree: 0%

---

# Più processi cron pianificati per lo stesso periodo di tempo

Questo articolo fornisce una patch per un problema noto di Adobe Commerce 2.2.2 relativo alla pianificazione di più processi cron contemporaneamente dopo la modifica delle variabili di tempo per alcune attività in Commerce Admin.

## Problema

Quando cron è configurato per essere eseguito ogni minuto, se si modificano le variabili di tempo per tre attività pianificate in Admin, il `cron_schedule` tabella di database mostra gruppi di più attività pianificate per essere eseguite contemporaneamente.

<u>Passaggi da riprodurre</u>:

1. In Commerce Admin, passa a **Negozi** > Impostazioni > **Configurazione** > **AVANZATE** > **Sistema** > **Cron (attività pianificate)** > **Opzioni di configurazione della tastiera per il gruppo: impostazione predefinita.**
1. Configura le seguenti opzioni:
   * **Pulizia cronologia ogni**: cancella **Usa sistema** e impostare su *1440*.
   * **Durata della cronologia di successo**: cancella **Usa sistema** e impostare su *1440*.
   * **Durata cronologia errori**: cancella **Usa sistema** e impostare su *1440*.

1. Clic **Salva configurazione**.
1. In SSH, esegui il `crontab -e` comando.
1. Imposta cron per l&#39;esecuzione ogni minuto.
1. Aprire tre finestre/schede terminali.
1. Passa a Adobe Commerce `root/base/project` in ciascuna finestra del terminale.
1. Esegui il comando seguente in ogni scheda/finestra:

   ```bash
   bin/magento cache:flush && bin/magento cron:run && bin/magento cache:flush && bin/magento cron:run
   ```

1. Passare a MySQL ed eseguire la query seguente:

   ```sql
   SELECT job_code, scheduled_at, count as count FROM cron_schedule GROUP BY job_code, scheduled_at HAVING count > 1 ORDER BY scheduled_at;
   ```

1. Vedere gruppi di attività pianificate per l&#39;esecuzione simultanea.

<u>Risultato previsto</u>: un cron `job_code` deve essere programmato per il periodo di tempo specificato.

<u>Risultato effettivo</u>: sono pianificati più processi cron per lo stesso periodo di tempo.

## Soluzione

Per Adobe Commerce sui commercianti con infrastrutture cloud, [aggiornamento degli strumenti ECE](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html) risolvere il problema.

Per risolvere il problema, i commercianti locali di Adobe Commerce devono applicare una delle patch allegate.

## Patch

Le patch sono allegate a questo articolo. Per scaricare, scorri verso il basso fino alla fine dell’articolo e fai clic sul nome del file, oppure fai clic su uno dei seguenti collegamenti:

* [Scarica MDVA-11304\_EE\_2.1.4\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.4_COMPOSER_v1.patch.zip)
* [Scarica MDVA-11304\_EE\_2.1.5\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.5_COMPOSER_v1.patch.zip)
* [Scarica MDVA-11304\_EE\_2.1.13\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.13_COMPOSER_v1.patch.zip)
* [Scarica MDVA-11304\_EE\_2.1.14\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.14_COMPOSER_v1.patch.zip)
* [Scarica MDVA-11304\_EE\_2.2.0\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.2.0_COMPOSER_v1.patch.zip)
* [Scarica MDVA-11304\_EE\_2.2\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.2.2_COMPOSER_v1.patch.zip)
* [Scarica MDVA-11304\_EE\_2.2.4\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.2.4_COMPOSER_v1.patch.zip)

### Versioni compatibili di Adobe Commerce

Le patch sono state create per una particolare versione indicata nel nome del file di patch. MDVA-11304\_EE\_2.2.4\_COMPOSER\_v1.patch è stato creato per Adobe Commerce 2.2.4 ed è la patch migliore da utilizzare per questa versione.

Le patch sono compatibili anche con le seguenti versioni:

* Per Adobe Commerce on-premise 2.1.0-2.1.4: [Scarica MDVA-11304\_EE\_2.1.4\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.4_COMPOSER_v1.patch.zip) La patch è compatibile (ma potrebbe non risolvere il problema) anche con le seguenti versioni ed edizioni di Adobe Commerce:
   * Adobe Commerce sull’infrastruttura cloud 2.1.0-2.1.4
* Per Adobe Commerce on-premise 2.1.5-2.1.12: [Scarica MDVA-11304\_EE\_2.1.5\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.5_COMPOSER_v1.patch.zip) La patch è compatibile (ma potrebbe non risolvere il problema) anche con le seguenti versioni ed edizioni di Adobe Commerce:
   * Adobe Commerce sull’infrastruttura cloud 2.1.5-2.1.12
* Per Adobe Commerce su infrastruttura cloud 2.1.13: [Scarica MDVA-11304\_EE\_2.1.13\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.13_COMPOSER_v1.patch.zip)
* Per Adobe Commerce on-premise 2.1.14-2.1.17: [Scarica MDVA-11304\_EE\_2.1.14\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.14_COMPOSER_v1.patch.zip) La patch è compatibile (ma potrebbe non risolvere il problema) anche con le seguenti versioni ed edizioni di Adobe Commerce:
   * Adobe Commerce on-premise 2.1.18
   * Adobe Commerce sull’infrastruttura cloud 2.1.14-2.1.18
* Per Adobe Commerce on-premise 2.2.0-2.2.1: [Scarica MDVA-11304\_EE\_2.2.0\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.2.0_COMPOSER_v1.patch.zip) La patch è compatibile (ma potrebbe non risolvere il problema) anche con le seguenti versioni ed edizioni di Adobe Commerce:
   * Adobe Commerce sull’infrastruttura cloud 2.2.0-2.2.1
* Per Adobe Commerce on-premise 2.2.0-2.2.3: [Scarica MDVA-11304\_EE\_2.2\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.2.2_COMPOSER_v1.patch.zip) La patch è compatibile (ma potrebbe non risolvere il problema) anche con le seguenti versioni ed edizioni di Adobe Commerce:
   * Adobe Commerce sull’infrastruttura cloud 2.2.0-2.2.3
* Per Adobe Commerce on-premise 2.2.4: [Scarica MDVA-11304\_EE\_2.2.4\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.2.4_COMPOSER_v1.patch.zip) La patch è compatibile (ma potrebbe non risolvere il problema) anche con le seguenti versioni ed edizioni di Adobe Commerce:
   * Adobe Commerce sull’infrastruttura cloud 2.2.4

## Come applicare il cerotto

Consulta [Come applicare una patch del compositore fornita da Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) nella knowledge base di supporto, per istruzioni.

## File allegati
