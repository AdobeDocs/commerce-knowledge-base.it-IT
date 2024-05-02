---
title: Installazione non riuscita. Impossibile creare install.log
description: Questo articolo fornisce una correzione per un’installazione non riuscita perché durante l’installazione non viene creato il file "install.log".
exl-id: ff614018-8e49-4170-a806-8ebdc91ae8a9
feature: Install, Logs, Upgrade
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# Installazione non riuscita. Impossibile creare install.log

In questo articolo viene fornita una correzione per un&#39;installazione non riuscita a causa della mancata creazione del `install.log` durante l&#39;installazione.

## Problema

L’esecuzione contemporanea di processi Adobe Commerce potrebbe causare problemi nella creazione del registro di installazione. Ad esempio, due installazioni diverse in schede separate.

## Causa

Installation-failed-cannot-create-install.log Verifica le impostazioni per `open_basedir` in `php.ini`. L&#39;Installazione guidata utilizza [sys\_get\_temp\_dir ( void )](https://php.net/manual/en/function.sys-get-temp-dir.php) Chiamata PHP per ottenere il valore della directory temporanea. Se [open\_basedir](http://php.net/manual/en/ini.core.php#ini.open-basedir) è impostato per rifiutare le connessioni a una directory specificata da `sys_get_temp_dir`, l&#39;installazione non riesce.
Controlla le impostazioni per `open_basedir` in `php.ini`. L&#39;Installazione guidata utilizza [sys\_get\_temp\_dir ( void )](https://php.net/manual/en/function.sys-get-temp-dir.php) Chiamata PHP per ottenere il valore della directory temporanea. Se [open\_basedir](https://php.net/manual/en/ini.core.php#ini.open-basedir) è impostato per rifiutare le connessioni a una directory specificata da `sys_get_temp_dir`, l&#39;installazione non riesce.


## Soluzione

Per risolvere il problema, modifica il valore di `open_basedir` e riavvia il server web.

Se non sai come modificare questo valore, procedi come segue:

1. Se non lo hai già fatto, crea [phpinfo.php](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/optional.html#install-optional-phpinfo).
1. Immetti il seguente URL nel campo indirizzo o percorso del browser: `https://<your web server IP or hostname>/<path to docroot>/phpinfo.php`
1. Cerca la posizione di `php.ini`.     `php.ini` viene in genere specificato come **File di configurazione caricato** nei risultati visualizzati.
1. In qualità di utente con privilegi di root, apri `php.ini` in un editor di testo.
1. Individua il valore di `open_basedir` e cambiarlo.
1. Salva le modifiche apportate a `php.ini`.
1. Riavviare il server Web.
