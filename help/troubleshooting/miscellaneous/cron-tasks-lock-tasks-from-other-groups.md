---
title: Le attività di controllo bloccano le attività da altri gruppi
description: Questo articolo fornisce una soluzione per il problema dell’infrastruttura cloud di Adobe Commerce on relativo a determinati processi cron a lungo termine che bloccano altri processi cron.
exl-id: b5b9e8b3-373c-4f93-af9c-85da84dbc928
feature: Configuration
role: Developer
source-git-commit: faa80e8233438fc15781341b3a9d5325269d6d20
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# Le attività di controllo bloccano le attività da altri gruppi

Questo articolo fornisce una soluzione per il problema dell’infrastruttura cloud di Adobe Commerce on relativo a determinati processi cron a lungo termine che bloccano altri processi cron.

## Prodotti e versioni interessati

* Architettura del piano Pro di Adobe Commerce su infrastruttura cloud
* A bordo prima di maggio 2019

## Problema

In Adobe Commerce for cloud, quando si dispone di attività cron complesse (attività a lungo termine), queste potrebbero bloccare altre attività per l’esecuzione. Ad esempio, l&#39;attività degli indicizzatori reindicizza gli indicizzatori invalidati. Il completamento può richiedere alcune ore e blocca altri processi cron predefiniti come l’invio di e-mail, la generazione di sitemap, notifiche ai clienti e altre attività personalizzate.

<u>Sintomi</u>:

I processi eseguiti dai processi cron non vengono eseguiti. Ad esempio, gli aggiornamenti dei prodotti non vengono applicati per ore o i clienti segnalano di non ricevere e-mail.

Quando si apre la tabella del database `cron_schedule`, vengono visualizzati i processi con stato `missed`.

## Causa

In precedenza, nel nostro ambiente cloud, il server Jenkins veniva utilizzato per eseguire processi cron. Jenkins eseguirà una sola istanza di un processo alla volta; di conseguenza, sarà in esecuzione un solo processo `bin/magento cron:run` alla volta.

## Soluzione

1. Contatta il [supporto Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) per abilitare i client autogestiti.
1. Modificare il file `.magento.app.yaml` nella directory radice del codice per Adobe Commerce nel ramo Git. Aggiungi quanto segue:

   ```yaml
     crons:
     cronrun:
     spec: "* * * * *"
     cmd: "php bin/magento cron:run"
   ```

1. Salva il file e invia gli aggiornamenti agli ambienti di staging e produzione (nello stesso modo in cui lo fai per gli ambienti di integrazione).

>[!NOTE]
>
>Non è necessario trasferire le vecchie configurazioni cron in cui sono presenti più `cron:run` alla nuova pianificazione cron; l&#39;attività `cron:run` regolare, aggiunta come descritto in precedenza, è sufficiente. Tuttavia, è necessario trasferire i tuoi processi personalizzati se ne avevi.

### Verifica se è stato abilitato il cron autogestito (solo per staging e produzione Cloud Pro)

Per verificare se il cron autogestito è abilitato, eseguire il comando `crontab -l` e osservare il risultato:

* Il cron autogestito è abilitato se è possibile visualizzare le attività, come indicato di seguito:

  ```bash
  username@hostname:~$ crontab -l    # Crontab is managed by the system, attempts to edit it directly will fail.
  SHELL=/etc/platform/username/cron-run    MAILTO=""    # m h dom mon dow job_name    * * * * * cronrun
  ```

* Il cron autogestito non è abilitato se non è possibile visualizzare le attività e ottenere il messaggio di errore *&quot;non è consentito utilizzare questo programma&quot;*.

>[!NOTE]
>
>Il comando sopra indicato per verificare se è abilitato il cron autogestito non è applicabile a un piano Starter e nell’ambiente di sviluppo/integrazione.

## Lettura correlata

* [Configura i processi cron](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) nella documentazione per gli sviluppatori.
