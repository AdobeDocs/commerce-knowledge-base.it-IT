---
title: Reindirizza al modulo di accesso dell’amministratore di Commerce con l’errore "La sessione corrente è scaduta"
description: '"Questo articolo illustra le possibili soluzioni per il problema di accesso dell’amministratore di Commerce, in cui si viene reindirizzati al modulo di accesso con il seguente messaggio di errore: *"La sessione corrente è scaduta"*. Le soluzioni includono la verifica dei problemi di impostazione dell''ora del server e la modifica delle impostazioni di archiviazione della sessione.'
exl-id: 29df2ed2-ff4a-4f1a-bdb7-1160416cda00
feature: Admin Workspace
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# Reindirizza al modulo di accesso dell’amministratore di Commerce con l’errore &quot;La sessione corrente è scaduta&quot;

In questo articolo vengono fornite le possibili soluzioni per il problema di accesso dell&#39;amministratore di Commerce, in cui si viene reindirizzati al modulo di accesso con il seguente messaggio di errore: *&quot;La sessione corrente è scaduta&quot;*. Le soluzioni includono la verifica dei problemi di impostazione dell&#39;ora del server e la modifica delle impostazioni di archiviazione della sessione.

## Edizioni e versioni interessate:

Tutte le versioni e le edizioni di Adobe Commerce

## Problema

<u>Passaggi da riprodurre</u>:

1. Vai alla pagina di amministrazione di Commerce.
1. Immetti le credenziali e fai clic su Accedi.

<u>Risultato previsto</u>:

Hai effettuato l’accesso a Commerce Admin.

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

Prova a modificare l’archivio della sessione. Utilizza le informazioni dell&#39;articolo [Come individuare i file di sessione](https://devdocs.magento.com/guides/v2.3/config-guide/sessions.html) nella documentazione per gli sviluppatori per scoprire dove è archiviata la sessione e modificarla modificando il file `app/etc/env.php`.

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

* [Importa dati dai file di configurazione](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-config-mgmt-import.html) nella documentazione per gli sviluppatori
* [Configurare Redis](https://devdocs.magento.com/guides/v2.3/config-guide/redis/config-redis.html) nella documentazione per gli sviluppatori
* [Errore &quot;L&#39;account è temporaneamente disabilitato&quot; durante il reindirizzamento al modulo di accesso dell&#39;amministratore di Commerce](/help/troubleshooting/miscellaneous/redirect-back-to-the-admin-login-form-with-your-account-is-temporarily-disabled-error.md) nella Knowledge Base del supporto tecnico
* [Reindirizza al modulo di accesso senza errori quando tenti di accedere all&#39;amministratore di Commerce](/help/troubleshooting/miscellaneous/login-redirect-when-trying-to-login-to-magento-admin.md) nella nostra knowledge base di supporto
