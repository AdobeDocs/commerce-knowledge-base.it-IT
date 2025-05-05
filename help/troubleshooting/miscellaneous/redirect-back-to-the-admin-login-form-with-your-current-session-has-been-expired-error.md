---
title: '''Reindirizza al modulo di accesso di [!UICONTROL Commerce Admin] con l''errore "La sessione corrente è scaduta"'
description: '''Questo articolo fornisce le possibili soluzioni per il problema di accesso [!UICONTROL Commerce Admin], in cui si viene reindirizzati al modulo di accesso con il seguente messaggio di errore: *"La sessione corrente è scaduta"*. Le soluzioni includono la verifica dei problemi di impostazione dell''ora del server e la modifica delle impostazioni di archiviazione della sessione.'
exl-id: 29df2ed2-ff4a-4f1a-bdb7-1160416cda00
feature: Admin Workspace
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# Reindirizza al modulo di accesso [!UICONTROL Commerce Admin] con l&#39;errore &quot;La sessione corrente è scaduta&quot;

Questo articolo fornisce le possibili soluzioni per il problema di accesso [!UICONTROL Commerce Admin], in cui si viene reindirizzati al modulo di accesso con il seguente messaggio di errore: *&quot;La sessione corrente è scaduta&quot;*. Le soluzioni includono la verifica dei problemi di impostazione dell&#39;ora del server e la modifica delle impostazioni di archiviazione della sessione.

## Edizioni e versioni interessate:

Tutte le versioni e le edizioni di Adobe Commerce

## Problema

<u>Passaggi da riprodurre</u>:

1. Passare alla pagina **[!UICONTROL Commerce Admin]**.
1. Immetti le tue credenziali e fai clic su **Accedi**.

<u>Risultato previsto</u>:

Si è connessi a [!UICONTROL Commerce Admin].

<u>Risultato effettivo</u>:

Sei stato reindirizzato al modulo di accesso, con il seguente messaggio di errore visualizzato: *&quot;La sessione corrente è scaduta&quot;*.

## Causa

Il problema potrebbe essere dovuto a due motivi:

* problema con le impostazioni dell&#39;ora del server
* un problema con l’archiviazione della sessione

Consulta la sezione seguente per informazioni sulle soluzioni.

## Soluzione

### Verifica la presenza di problemi relativi alle impostazioni dell&#39;ora del server

Controllare il record di sessione creato nella tabella `admin_user_session`. Se i valori di `created_at` e/o `updated_at` non sono corretti, la causa potrebbe essere il problema con le impostazioni dell&#39;ora del server. Chiedere all&#39;amministratore del sistema del server di verificare tale condizione. L’ora in DB è impostata su UTC per impostazione predefinita.

### Modificare l’archiviazione della sessione

Prova a modificare l’archivio della sessione. Utilizza le informazioni dell&#39;articolo [Come individuare i file di sessione](https://experienceleague.adobe.com/it/docs/commerce-operations/configuration-guide/storage/session-storage/sessions) nella documentazione per gli sviluppatori per scoprire dove è archiviata la sessione e modificarla modificando il file `app/etc/env.php`.

Ad esempio, per iniziare a memorizzare la sessione nel file system, modificare la sezione `'session'` come segue:

```php
....
'session' =>
    array (
      'save' => 'files',
),
....
```

Eseguire il comando `bin/magento app:config:import` per importare i dati di configurazione.


## Lettura correlata

* [Importa dati dai file di configurazione](https://experienceleague.adobe.com/it/docs/commerce-operations/configuration-guide/cli/configuration-management/import-configuration) nella documentazione per gli sviluppatori
* [Configura [!DNL Redis]](https://experienceleague.adobe.com/it/docs/commerce-operations/configuration-guide/cache/redis/config-redis) nella documentazione per gli sviluppatori
* [Reindirizzamento al modulo di accesso di [!UICONTROL Commerce Admin] con l&#39;errore &quot;L&#39;account è temporaneamente disabilitato&quot;](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/redirect-back-to-the-admin-login-form-with-your-account-is-temporarily-disabled-error) nella Knowledge Base di supporto
* [Reindirizzare al modulo di accesso senza errori quando si tenta di accedere a [!UICONTROL Commerce Admin]](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/login-redirect-when-trying-to-login-to-magento-admin) nella Knowledge Base di supporto
* [Best practice per la modifica delle tabelle del database](https://experienceleague.adobe.com/it/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) nel playbook di implementazione di Commerce

