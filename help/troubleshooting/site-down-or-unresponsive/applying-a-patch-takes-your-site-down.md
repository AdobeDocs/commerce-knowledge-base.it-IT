---
title: L’applicazione di una patch blocca il sito
description: Questo articolo parla del problema in cui una patch appena applicata distrugge il sito. Per risolvere il problema, è possibile rimuovere la patch.
exl-id: dc765bcd-0761-4efd-a345-46a908d61272
feature: Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# L’applicazione di una patch blocca il sito

Questo articolo parla del problema in cui una patch appena applicata distrugge il sito. Per risolvere il problema, è possibile rimuovere la patch.

## Prodotti e versioni interessati

* Adobe Commerce (tutti i metodi di distribuzione), tutte le versioni supportate
* Magento Open Source, tutte le versioni

## Problema

Dopo aver applicato un cerotto, il sito si oscura.

## Causa

Questo problema potrebbe essere dovuto a un’incompatibilità di versione tra la patch appena applicata al sito web, le personalizzazioni, altre patch applicate in passato o a un altro errore.

## Soluzione

Rimuovere la patch. Il metodo di rimozione delle patch è diverso per l’infrastruttura cloud di Adobe Commerce rispetto a Adobe Commerce on-premise e Magento Open Source.

### Magento Open Source, tutte le versioni 1.X

Per le versioni di Magento Open Source 1.X,

* Esegui il seguente comando SSH: `h SUPEE_patch --revert `

### Adobe Commerce on-premise, Magento Open Source, tutte le versioni 2.x

Per le versioni on-premise e Magento Open Source 2.x di Adobe Commerce,

1. Esegui il seguente comando SSH:

   ```
   patch -p1 -R %patch_name%.composer.patch
   ```

   Se il comando precedente non funziona, provare a utilizzare `-p2` invece di `-p1`)

1. Affinché le modifiche vengano applicate, aggiorna la cache in Admin in **Sistema** > **Gestione cache**.

### Adobe Commerce su infrastruttura cloud, tutte le versioni

Per Adobe Commerce su infrastruttura cloud, tutte le versioni,

1. Rimuovi il `%patch_name%.composer.patch` file da `m2-hotfixes` directory.
1. Effettua il commit e invia le modifiche al codice:

   ```
   git commit -m "Remove %patch_name%.composer.patch patch" && git push origin
   ```

## Lettura correlata

* [Come applicare una patch del compositore fornita dall&#39;Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) nella nostra knowledge base di supporto.
