---
title: Problemi relativi ai plug-in del compositore durante l’aggiornamento ad Adobe Commerce 2.4.4
description: Questo articolo fornisce una soluzione per evitare il problema relativo ai plug-in del compositore durante l’aggiornamento da Adobe Commerce 2.4.3 e versioni precedenti a Adobe Commerce 2.4.4 o versioni successive (quando vengono rilasciate versioni future).
exl-id: 7502ca9e-c307-4e8a-aa1d-4886e7be25da
feature: Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 0%

---

# Problemi relativi ai plug-in del compositore durante l’aggiornamento ad Adobe Commerce 2.4.4

Questo articolo fornisce una soluzione per evitare problemi con i plug-in del compositore durante l’aggiornamento da Adobe Commerce 2.4.3 e versioni precedenti a Adobe Commerce 2.4.4 o versioni successive (quando vengono rilasciate versioni future).

## Prodotti e versioni interessati

* Adobe Commerce on-premise, qualsiasi versione quando si aggiornava alla versione 2.4.4 o successiva (quando rilasciata)
* Adobe Commerce su infrastruttura cloud, qualsiasi versione durante l’aggiornamento alla versione 2.4.4 o successiva (quando rilasciata)
* Magento Open Source, qualsiasi versione quando si aggiorna alla versione 2.4.4 o successiva (quando rilasciata)

## Problema

Durante l’aggiornamento a Adobe Commerce 2.4.4 o versione successiva dopo luglio 2022, è possibile che il compositore riceva un avviso relativo ai plug-in.

<u>Passaggi da riprodurre</u>:

Prerequisiti: è installato Adobe Commerce 2.4.3 o versione precedente.

1. Avviare l&#39;aggiornamento come descritto in [Eseguire un aggiornamento](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html?lang=it).
1. Eseguire il comando `composer update` per aggiornare l&#39;applicazione Adobe Commerce.

<u>Risultati previsti</u>:

Aggiornamento completato.

<u>Risultati effettivi</u>:

L’installazione non riesce e viene visualizzato un errore simile al seguente:

```bash
Writing lock file
Installing dependencies from lock file (including require-dev)
Package operations: 591 installs, 0 updates, 0 removals
  - Installing laminas/laminas-dependency-plugin (2.2.0): Extracting archive
laminas/laminas-dependency-plugin contains a Composer plugin which is currently not in your allow-plugins config. See https://getcomposer.org/allow-plugins
Do you trust "laminas/laminas-dependency-plugin" to execute code and wish to enable it now? (writes "allow-plugins" to composer.json) [y,n,d,?] y
Plugin initialization failed (require(app/etc/NonComposerComponentRegistration.php): failed to open stream: No such file or directory), uninstalling plugin
  - Removing laminas/laminas-dependency-plugin (2.2.0)
    Install of laminas/laminas-dependency-plugin failed


  [ErrorException]
  require(app/etc/NonComposerComponentRegistration.php): failed to open stream: No such file or directory
```

## Causa

Dopo luglio 2022 Composer modifica il valore predefinito dell&#39;opzione [`allow-plugins`](https://getcomposer.org/doc/06-config.md#allow-plugins) in `{}` e i plug-in non verranno più caricati se non consentito.

## Soluzione

Aggiungi quanto segue al file `composer.json`, a seconda di come hai installato Adobe Commerce:

* Se il progetto è stato creato [utilizzando il comando `composer create-project`](https://experienceleague.adobe.com/it/docs/commerce-operations/installation-guide/composer#get-the-metapackage):

  ```json
  "config": {
      "allow-plugins": {
          "dealerdirect/phpcodesniffer-composer-installer": true,
          "laminas/laminas-dependency-plugin": true,
          "magento/*": true
      }
  }
  ```

* Se il progetto è stato creato in un altro modo e non dispone di `"dealerdirect/phpcodesniffer-installer"` nella sezione `"require-dev"`:

  ```json
  "config": {
      "allow-plugins": {
          "laminas/laminas-dependency-plugin": true,
          "magento/*": true
      }
  }
  ```

Dopo aver aggiornato il file `composer.json`, eseguire il comando `composer update` e riavviare il processo di aggiornamento.
