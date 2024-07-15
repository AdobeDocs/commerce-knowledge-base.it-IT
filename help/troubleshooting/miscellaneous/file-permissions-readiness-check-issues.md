---
title: Problemi di verifica della preparazione delle autorizzazioni dei file
description: '"Questo articolo fornisce una correzione per i problemi relativi al controllo di preparazione delle autorizzazioni dei file. Le directory nel file system di Adobe Commerce devono essere scrivibili dall’utente del server web e dal proprietario del file system di Adobe Commerce, se applicabile. Se le autorizzazioni non sono impostate correttamente, nell''Installazione guidata Web viene visualizzato un errore simile al seguente:'''
exl-id: 252e6e7d-5269-44ce-b3ce-6fc2ea6a1c5c
feature: Roles/Permissions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# Problemi di verifica della preparazione delle autorizzazioni dei file

Questo articolo fornisce una correzione per i problemi relativi al controllo di preparazione delle autorizzazioni dei file. Le directory nel file system di Adobe Commerce devono essere scrivibili dall’utente del server web e dal proprietario del file system di Adobe Commerce, se applicabile. Se le autorizzazioni non sono impostate correttamente, nell&#39;Installazione guidata Web viene visualizzato un errore simile al seguente:

![install_rc_file-perms.png](assets/install_rc_file-perms.png)

La modalità di risoluzione del problema dipende dalla configurazione con un solo utente o con due utenti:

* *Un utente* significa che si accede al server Adobe Commerce come lo stesso utente che esegue anche il server Web. Questo tipo di configurazione è comune negli ambienti di hosting condivisi.
* *Due utenti* indicano che in genere *non è possibile* accedere come utente del server Web o passare a tale utente. In genere si accede come un utente ed il server web viene eseguito come un altro utente. Questo è tipico nell&#39;hosting privato o se disponi di un server personalizzato.

## Risoluzione per un solo utente

Se si dispone dell&#39;accesso alla riga di comando, immettere il comando seguente presupponendo che Adobe Commerce sia installato in `/var/www/html/magento2`:

```bash
$ cd /var/www/html/magento2 && find var vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && find var vendor pub/static pub/media app/etc -type d -exec chmod g+w {} + && chmod u+x bin/magento
```

Se non disponi dell’accesso alla riga di comando, utilizza un client FTP o un’applicazione di gestione file fornita dal provider di hosting per impostare le autorizzazioni.

## Risoluzione per due utenti

Per immettere facoltativamente tutti i comandi su una riga, immettere il seguente presupposto: Adobe Commerce è installato in `/var/www/html/magento2` e il nome del gruppo di server Web è `apache`:

```bash
$ cd /var/www/html/magento2 && find var vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && find var vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && chown -R :apache . && chmod u+x bin/magento
```

Nel caso in cui le autorizzazioni del file system dell&#39;evento non siano impostate correttamente e non possano essere modificate dal proprietario del file system Adobe Commerce, è possibile immettere il comando come utente con privilegi `root`:

```bash
$ cd /var/www/html/magento2 && sudo find var vendor
  pub/static pub/media app/etc -type f -exec chmod g+w {} + && sudo find
  var vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + &&
  sudo chown -R :apache . && sudo chmod u+x bin/magento
```
