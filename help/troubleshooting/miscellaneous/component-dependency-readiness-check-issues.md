---
title: Problemi di verifica della preparazione delle dipendenze dei componenti
description: Questo articolo fornisce soluzioni per i conflitti di dipendenza dei componenti.
exl-id: e0865226-2aaf-4bdd-8c28-28f32f38ce0c
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---

# Problemi di verifica della preparazione delle dipendenze dei componenti

Questo articolo fornisce soluzioni per i conflitti di dipendenza dei componenti.

## Risolvere i conflitti di dipendenza dei componenti {#resolve-component-dependency-conflicts}

Si consiglia di provare le soluzioni seguenti nell&#39;ordine indicato:

1. [Dipendenze in conflitto](#trouble-depend-conflict)
1. [Problemi relativi alle autorizzazioni del file system](#trouble-depend-permission)
1. [Lo stato di Verifica dipendenza componente non cambia mai](#trouble-depend-state)

### Dipendenze in conflitto {#trouble-depend-conflict}

Viene visualizzato il messaggio *Sono state trovate dipendenze dei componenti in conflitto* se Composer non è in grado di determinare quali componenti installare o aggiornare. Per risolvere i problemi di dipendenza dei componenti, devi essere una persona tecnica che capisca a fondo come funziona Compositore.

Di seguito è riportato un esempio di messaggio di errore:

```bash
We found conflicting component dependencies.
 You are trying to update package(s) magento/module-sample-data to 1.0.0-beta
 We've detected conflicts with the following packages:
 - magento/sample-data version 0.74.0-beta15. Please try to update it to one of the following package versions: 0.74.0-beta16, 0.74.0-beta14, 0.74.0-beta13, 0.74.0-beta12, 0.74.0-beta11, 0.74.0-beta10, 0.74.0-beta9, 0.74.0-beta8, 0.74.0-beta7
```

>[!NOTE]
>
>Il messaggio visualizzato sarà probabilmente diverso.

Consulta [Dipendenze dei componenti in conflitto per una soluzione](/help/troubleshooting/miscellaneous/conflicting-component-dependencies.md) nella Knowledge Base di supporto.

## Problemi relativi alle autorizzazioni del file system {#trouble-depend-permission}

Se il proprietario del file system di Adobe Commerce non dispone delle autorizzazioni necessarie per scrivere nelle directory del file system di Adobe Commerce, viene visualizzato un messaggio simile al seguente:

```bash
file_put_contents(/var/www/html/magento2/var/composer_home/cache/repo/https---
packagist.org/provider-doctrine$instantiator.json): failed to open stream: Permission denied
```

Assicurati di impostare le autorizzazioni del file system come descritto nell&#39;articolo [Panoramica sulla proprietà e sulle autorizzazioni](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/file-system/overview) nella documentazione per gli sviluppatori.

## Lo stato di Verifica dipendenza componente non cambia mai {#trouble-depend-state}

In alcuni casi, lo stato del controllo di dipendenza dei componenti non cambia, anche dopo aver tentato di correggere i problemi. In tal caso, è possibile eliminare o rinominare i file denominati `<magento_root>/var/.update_cronjob_status` e `<magento_root>/var/.setup_cronjob_status` e provare a eseguire nuovamente Gestione componenti.

La ridenominazione o la rimozione di questi file costringe Component Manager a eseguire nuovamente i controlli.
