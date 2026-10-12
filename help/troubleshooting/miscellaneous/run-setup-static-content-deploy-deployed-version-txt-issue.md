---
title: eseguire il problema "setup:static-content:deploy" deployed_version.txt
description: 'Questo articolo fornisce una correzione per "deployed_version.txt": errore non scrivibile quando si esegue manualmente il comando "setup:static-content:deploy".'
exl-id: 88d8c126-349f-49cd-8f02-2a32e4994521
feature: Deploy, Page Content, SCD
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: 17d326fa-534a-55a5-b46f-8ae1de1e2f75
    internal-label: Page Content
  - id: d05f97c9-0a96-5792-92cf-f66ce7326e3a
    internal-label: SCD
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%
---
# esegui `setup:static-content:deploy` problema deployed_version.txt

Questo articolo fornisce una correzione per l&#39;errore non scrivibile di `deployed_version.txt` durante l&#39;esecuzione manuale del comando `setup:static-content:deploy`.

## Problema

Se si seguono le raccomandazioni di Adobe Commerce sull&#39;infrastruttura cloud per utilizzare la gestione della configurazione (e si sposta la generazione di risorse statiche nella fase di build per ridurre i tempi di inattività del sito web durante la distribuzione), è possibile che si verifichi il seguente errore durante l&#39;esecuzione manuale del comando `setup:static-content:deploy`:

```
{{cloud-project-id}}_stg@i:~$ php bin/magento setup:static-content:deploy
Requested languages: en_US
Requested areas: frontend, adminhtml
Requested themes: Magento/blank, Magento/luma, Aheadworks/marketplace, Magento/backend
[Magento\Framework\Exception\FileSystemException]
The path "deployed_version.txt:///app/{{cloud-project-id}}_stg/pub/static/app/{{cloud-project-id}}_stg/pub/static/" is not writable
```

## Causa

Abbiamo ottimizzato il processo di distribuzione per ridurre i tempi di inattività e creato collegamenti simbolici ai file di risorse statiche invece di copiarli. La posizione in cui sono memorizzate le risorse statiche è di sola lettura, ecco perché viene visualizzato il messaggio di errore riportato sopra.

Si sconsiglia vivamente di eseguire la distribuzione manuale del contenuto statico, in quanto tutte le risorse sono già generate e non vi saranno differenze tra i file se lo si esegue manualmente (anche i file dei temi sono di sola lettura, non è possibile modificarli), quindi tale operazione non ha alcun senso.

## Soluzione

Se si desidera comunque eseguire la distribuzione del contenuto statico, rimuovere i symlink nella directory `pub/static` ed eseguire di nuovo il comando `setup:static-content:deploy`:

```
find pub/static/ -maxdepth 1 -type l -delete
```
