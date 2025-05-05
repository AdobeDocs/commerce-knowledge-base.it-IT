---
title: Download non riuscito a causa di modifiche nel Compositore
description: Questo articolo fornisce una correzione per un errore di download e di eccezione di Adobe Commerce non riuscito.
exl-id: 5abdab97-4b0c-466b-a68f-a2637d2826e5
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---

# Download non riuscito a causa di modifiche nel Compositore

Questo articolo fornisce una correzione per un errore di download e di eccezione di Adobe Commerce non riuscito.

## Problema

Durante il download viene visualizzato il seguente errore:

```php
[ErrorException]
  file_get_contents(app/etc/NonComposerComponentRegistration.php): failed to open stream: No such file or directory
```

## Causa

Ciò si verifica a causa di modifiche apportate ad alcune versioni di Composer. Per ovviare a questo problema, devi effettuare il downgrade di Composer a una versione precedente e riprovare a scaricare Adobe Commerce.

## Soluzione

Qualsiasi versione di Composer datata tra il 21 novembre e il 26 novembre 2015 ha questo problema. Per confermare che il problema è relativo alla versione del Compositore, immetti il comando seguente:

```php
composer -v
```

La versione visualizzata è simile alla seguente:

```php
Composer version 1.0-dev (2b14f0a047dd4f3545ec82381f65c36ea93a4c81) 2015-11-25 17:13:09
```

Nota che la data è 2015-11-25, che indica che Composer ha questo problema.

Per aggirare il problema:

1. Modifica la versione di Composer per consentirti di scaricare il software Adobe Commerce eseguendo una delle seguenti operazioni:

   * Eseguire il downgrade del Compositore utilizzando il comando seguente: `composer self-update 1.0.0-alpha11`.
   * Aggiornare Compositore a una versione successiva al 26 novembre 2015: `composer self-update`.

1. Elimina la directory e le sottodirectory di Adobe Commerce.
1. Riprovare il download utilizzando `[composer create-project](https://experienceleague.adobe.com/it/docs/commerce-operations/installation-guide/composer)` o `[git clone](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)`.
1. Dopo aver scaricato correttamente il software Adobe Commerce, aggiornare Compositore: `composer self-update`.
