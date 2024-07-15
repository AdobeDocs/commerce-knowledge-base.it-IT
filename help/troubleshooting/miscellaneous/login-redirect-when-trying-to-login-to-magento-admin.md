---
title: Reindirizzamento accesso quando si tenta di accedere ad Amministratore Commerce
description: Questo articolo illustra le possibili soluzioni per il problema di accesso dell’amministratore di Commerce, in cui vieni reindirizzato al modulo di accesso quando tenti di accedere all’amministratore e non viene visualizzato alcun messaggio di errore. Ad esempio, puoi correggere le impostazioni del fuso orario del server e cancellare le impostazioni dei cookie in Adobe Commerce.
exl-id: ff3114fd-8690-4983-8221-cf807f083b15
feature: Admin Workspace, Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# Reindirizzamento accesso quando si tenta di accedere ad Amministratore Commerce

Questo articolo illustra le possibili soluzioni per il problema di accesso dell’amministratore di Commerce, in cui vieni reindirizzato al modulo di accesso quando tenti di accedere all’amministratore e non viene visualizzato alcun messaggio di errore. Ad esempio, puoi correggere le impostazioni del fuso orario del server e cancellare le impostazioni dei cookie in Adobe Commerce.

## Edizioni e versioni interessate:

Tutte le versioni e le edizioni di Adobe Commerce.

## Problema

<u>Passaggi da riprodurre</u>:

1. Vai alla pagina dell’amministratore di Commerce.
1. Immetti le credenziali e fai clic su Accedi.

<u>Risultati previsti</u>:

Hai effettuato l’accesso a Commerce Admin.

<u>Risultati effettivi</u>:

Si viene reindirizzati al modulo di accesso senza messaggi di errore.

## Causa

Il problema può essere dovuto a due motivi:

* Fuso orario errato impostato a livello di browser (il che porta a considerare la sessione di amministrazione scaduta anche se la sua durata effettiva non è ancora scaduta).
* Impostazioni dei cookie non corrette. In tal caso, Adobe Commerce non utilizza la sessione stabilita.

Vedere i paragrafi successivi per le soluzioni in ogni caso.

## Soluzioni

### Problema di durata della sessione di amministrazione

Prova a utilizzare un browser diverso e aumenta la durata della sessione di amministrazione se è inferiore a un’ora.

Per aumentare la durata della sessione di amministrazione, effettua le seguenti operazioni:

1. Creare un backup del database.
1. Utilizza uno strumento di database come [phpMyAdmin](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/optional.html#install-optional-phpmyadmin) oppure accedi al database manualmente dalla riga di comando per eseguire la seguente query SQL:

   ```sql
   UPDATE core_config_data SET value = 7200 WHERE path = 'admin/security/session_lifetime';
   ```

1. Pulisci la cache di configurazione eseguendo il comando seguente:

   ```bash
   php <your_magento_install_dir>/bin/magento cache:clean config
   ```

### Impostazioni dei cookie non corrette

Per verificare e cancellare i valori delle impostazioni dei cookie, effettua le seguenti operazioni:

1. Creare un backup del database.
1. Utilizza uno strumento di database come [phpMyAdmin](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/optional.html#install-optional-phpmyadmin) oppure accedi al database manualmente dalla riga di comando per eseguire la seguente query SQL:

   ```sql
   SELECT * FROM core_config_data WHERE (path = "web/cookie/cookie_domain" OR path = "web/cookie/cookie_path");
   ```

1. Se le risposte dei valori non sono vuote, impostarle su NULL eseguendo il comando seguente:

   ```sql
   UPDATE core_config_data SET value = NULL WHERE (path = "web/cookie/cookie_domain" OR path = "web/cookie/cookie_path");
   ```

1. Pulisci la cache di configurazione eseguendo il comando seguente:

   ```bash
   php <your_magento_install_dir>/bin/magento cache:clean config
   ```

## Articoli correlati

* [Errore &quot;Il tuo account è temporaneamente disabilitato&quot;](/help/troubleshooting/miscellaneous/redirect-back-to-the-admin-login-form-with-your-account-is-temporarily-disabled-error.md) nella Knowledge Base di supporto per reindirizzare nuovamente al modulo di accesso dell&#39;amministratore.
* [Errore &quot;La sessione corrente è scaduta&quot;](/help/troubleshooting/miscellaneous/redirect-back-to-the-admin-login-form-with-your-current-session-has-been-expired-error.md) nella Knowledge Base di supporto per il reindirizzamento al modulo di accesso dell&#39;amministratore.
