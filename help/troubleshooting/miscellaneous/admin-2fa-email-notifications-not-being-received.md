---
title: Notifiche e-mail di Admin 2FA non ricevute
description: Questo articolo fornisce informazioni per la risoluzione dei problemi quando non ricevi l’e-mail con le istruzioni di completamento dell’installazione dopo aver configurato Two-Factor Authentication (2FA) per migliorare la sicurezza dell’accesso amministratore in Adobe Commerce sull’infrastruttura cloud.
exl-id: 7ab6b2b4-6aca-4323-a45b-2b4e52955160
feature: Admin Workspace, Communications
role: Developer
source-git-commit: 435a545adcf2a1d6b023abaec55c4b73e942ee1a
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---

# Notifiche e-mail di Admin 2FA non ricevute


## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud, tutte le versioni

## Problema

Hai impostato l’autenticazione a due fattori per migliorare la sicurezza degli accessi amministratore, ma non ricevi l’e-mail con le istruzioni per il completamento della configurazione.

## Causa

Se l&#39;e-mail del mittente non è stata configurata correttamente o il dominio non è stato contrassegnato con un&#39;etichetta bianca in SendGrid, è probabile che l&#39;e-mail sia finita nella cartella Spam.

## Risoluzione dei problemi

### Passaggio 1: verifica la cartella Spam

1. Se l’e-mail non è stata visualizzata nella cartella Spam, esegui questa query Mysql per verificare che gli indirizzi e-mail siano stati configurati:

   ```sql
   select * from core_config_data where path like '%trans_email%';
   ```

   * Se non restituisce alcun risultato, significa che l’indirizzo del mittente non è stato configurato.
Poiché non hai accesso all’amministratore, dovrai inserire la configurazione nel database. Inserire l&#39;indirizzo e-mail appropriato ed eseguire l&#39;istruzione MySQL:

   ```
   insert into core_config_data (scope,scope_id,path,value) values ('default',0,'trans_email/ident_general/email', your-email@here.com)
   ```

   * Se restituisce un risultato, passare al **passaggio 2**.

1. Se l’e-mail è apparsa nella cartella Spam, fai clic sul collegamento nell’e-mail. Se il collegamento è scaduto, prova ad accedere di nuovo per ripetere la procedura.
1. Una volta ottenuto l&#39;accesso, vai a **Archivi** > **Configurazione** > **Generale** > **Archivia indirizzi e-mail** e configura gli indirizzi e-mail.

### Passaggio 2: se/una volta configurati correttamente gli indirizzi e-mail, SSH nell’ambiente ed esegui questo comando:

```php
php -r "mail(<your email address>,<subject>,<content>,'To: <sender email>');"
```

Controlla la cartella Spam per l’e-mail. Se l&#39;e-mail viene visualizzata, [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#login) per richiedere che il dominio sia contrassegnato con un&#39;etichetta bianca in SendGrid.

## Lettura correlata

* [SendGrid](https://devdocs.magento.com/cloud/project/sendgrid.html) nella documentazione per gli sviluppatori.
