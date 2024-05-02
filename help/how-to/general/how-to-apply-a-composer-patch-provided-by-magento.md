---
title: Come applicare una patch del compositore fornita dall'Adobe
description: Questo articolo spiega come applicare una patch del compositore per Adobe Commerce on-premise, Adobe Commerce su infrastruttura cloud e Magento Open Source.
exl-id: a9301ad8-1d4b-49f5-b679-758624928219
feature: Cache
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# Come applicare una patch del compositore fornita dall&#39;Adobe

Questo articolo spiega come applicare una patch del compositore per Adobe Commerce on-premise, Adobe Commerce su infrastruttura cloud e Magento Open Source.

>[!WARNING]
>
>Si consiglia vivamente di applicare e testare la patch nell’ambiente di staging/integrazione prima di applicarla alla produzione. Consigliamo inoltre di avere un backup recente prima di qualsiasi manipolazione.

## Applicare una patch del compositore per Adobe Commerce sull’infrastruttura cloud {#cloud}

1. Se non si dispone di una directory denominata `m2-hotfixes` nella directory principale del progetto, creane una.
1. Copia il `%patch_name%.composer.patch` file al `m2-hotfixes` directory.
1. Aggiungi, esegui il commit e invia le modifiche al codice:

   ```git
   git add -A
   ```

   ```git
   git commit -m "Apply %patch_name%.composer.patch patch"
   ```

   ```git
   git push origin
   ```

Per ulteriori informazioni sull’applicazione di patch ai progetti Cloud, consulta [Applicare le patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

### Come applicare una patch del compositore per Adobe Commerce on-premise e Magento Open Source {#commerce}

1. Carica la patch nella directory principale di Adobe Commerce locale o del Magento Open Source.
1. Esegui il seguente comando SSH:

   ```bash
   patch -p1 < %patch_name%.composer.patch
   ```

   Se il comando precedente non funziona, provare a utilizzare `-p2` invece di `-p1` )

1. Affinché le modifiche vengano applicate, aggiorna la cache in Admin in **Sistema** > **Gestione cache**.
