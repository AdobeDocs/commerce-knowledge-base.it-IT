---
title: L’applicazione di una patch blocca il sito
description: Questo articolo parla del problema in cui una patch appena applicata distrugge il sito. Per risolvere il problema, è possibile rimuovere la patch.
exl-id: dc765bcd-0761-4efd-a345-46a908d61272
feature: Cache
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '289'
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

* Esegui il comando SSH seguente: `h SUPEE_patch --revert `

### Adobe Commerce on-premise, Magento Open Source, tutte le versioni 2.x

Per le versioni on-premise di Adobe Commerce e Magento Open Source 2.x,

1. Esegui il seguente comando SSH:

   ```
   patch -p1 -R %patch_name%.composer.patch
   ```

   Se il comando precedente non funziona, provare a utilizzare `-p2` anziché `-p1`

1. Affinché le modifiche vengano applicate, aggiorna la cache nell&#39;amministratore in **Sistema** > **Gestione cache**.

### Adobe Commerce su infrastruttura cloud, tutte le versioni

Per Adobe Commerce su infrastruttura cloud, tutte le versioni,

1. Rimuovere i file `%patch_name%.composer.patch` dalla directory `m2-hotfixes`.
1. Effettua il commit e invia le modifiche al codice:

   ```
   git commit -m "Remove %patch_name%.composer.patch patch" && git push origin
   ```

## Lettura correlata

* [Come applicare una patch del compositore fornita da Adobe](https://experienceleague.adobe.com/it/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/how-to-apply-a-composer-patch-provided-by-magento) nella Knowledge Base di supporto.
