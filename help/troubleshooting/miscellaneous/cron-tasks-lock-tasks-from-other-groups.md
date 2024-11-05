---
title: '[!DNL Cron] attività bloccano le attività da altri gruppi'
description: Questo articolo fornisce una soluzione per il problema dell'infrastruttura cloud di Adobe Commerce relativo ad alcuni [!DNL cron] processi a lungo termine che bloccano altri [!DNL cron] processi.
exl-id: b5b9e8b3-373c-4f93-af9c-85da84dbc928
feature: Configuration
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# [!DNL Cron] attività bloccano le attività da altri gruppi

Questo articolo fornisce una soluzione per il problema dell&#39;infrastruttura cloud di Adobe Commerce relativo ad alcuni processi di [!DNL cron] a lungo termine che bloccano altri processi di [!DNL cron].

## Prodotti e versioni interessati

* Architettura del piano Pro di Adobe Commerce su infrastruttura cloud
* A bordo prima di maggio 2019

## Problema

In Adobe Commerce for cloud, quando si dispone di [!DNL cron] attività complesse (attività a lungo termine), queste potrebbero bloccare altre attività per l&#39;esecuzione. Ad esempio, l&#39;attività degli indicizzatori reindicizza gli indicizzatori invalidati. Il completamento può richiedere alcune ore e bloccherà altri processi predefiniti di [!DNL cron] come l&#39;invio di e-mail, la generazione di sitemap, notifiche ai clienti e altre attività personalizzate.

<u>Sintomi</u>:

I processi eseguiti da [!DNL cron] processi non vengono eseguiti. Ad esempio, gli aggiornamenti dei prodotti non vengono applicati per ore o i clienti segnalano di non ricevere e-mail.

Quando si apre la tabella del database `cron_schedule`, vengono visualizzati i processi con stato `missed`.

## Causa

In precedenza, nel nostro ambiente cloud, il server Jenkins veniva utilizzato per eseguire [!DNL cron] processi. Jenkins eseguirà una sola istanza di un processo alla volta; di conseguenza, sarà in esecuzione un solo processo `bin/magento cron:run` alla volta.

## Soluzione

1. Contatta il [supporto Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) per abilitare [!DNL crons] gestito autonomamente.
1. Modificare il file `.magento.app.yaml` nella directory radice del codice per Adobe Commerce nel ramo [!DNL Git]. Aggiungi quanto segue:

   ```yaml
     crons:
     cronrun:
     spec: "* * * * *"
     cmd: "php bin/magento cron:run"
   ```

1. Salva il file e invia gli aggiornamenti agli ambienti di staging e produzione (nello stesso modo in cui lo fai per gli ambienti di integrazione).

>[!NOTE]
>
>Non è necessario trasferire le vecchie configurazioni di [!DNL cron] in cui sono presenti più `cron:run` alla nuova pianificazione di [!DNL cron]. L&#39;attività regolare di `cron:run`, aggiunta come descritto in precedenza, è sufficiente. Tuttavia, è necessario trasferire i tuoi processi personalizzati se ne avevi.

### Controlla se hai abilitato [!DNL cron] gestito autonomamente (solo per staging e produzione Cloud Pro)

Per verificare se [!DNL cron] gestito in modo autonomo è abilitato, eseguire il comando `crontab -l` e osservare il risultato:

* [!DNL cron] autogestito è abilitato se si è in grado di visualizzare le attività, come indicato di seguito:

  ```bash
  username@hostname:~$ crontab -l    # Crontab is managed by the system, attempts to edit it directly will fail.
  SHELL=/etc/platform/username/cron-run    MAILTO=""    # m h dom mon dow job_name    * * * * * cronrun
  ```

* [!DNL cron] gestito automaticamente non è abilitato se non si è in grado di visualizzare le attività e ottenere il messaggio di errore *&quot;non è consentito utilizzare questo programma&quot;*.

>[!NOTE]
>
>Il comando sopra indicato per verificare se è abilitato il [!DNL cron] gestito in modo autonomo non è applicabile a un piano Starter e all&#39;ambiente di sviluppo/integrazione.

## Lettura correlata

* [Configura [!DNL cron] processi](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) nella documentazione per gli sviluppatori
* [Best practice per la modifica delle tabelle del database](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) nel playbook di implementazione di Commerce
