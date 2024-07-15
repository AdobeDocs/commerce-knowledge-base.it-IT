---
title: esegui il problema 'setup:static-content:deploy` deployed_version.txt
description: 'Questo articolo fornisce una correzione per "deployed_version.txt": errore non scrivibile quando si esegue manualmente il comando "setup:static-content:deploy".'
exl-id: 88d8c126-349f-49cd-8f02-2a32e4994521
feature: Deploy, Page Content, SCD
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 0%

---

# esegui `setup:static-content:deploy` problema deployed_version.txt

Questo articolo fornisce una correzione per l&#39;errore non scrivibile di `deployed_version.txt` durante l&#39;esecuzione manuale del comando `setup:static-content:deploy`.

## Problema

Se si seguono le raccomandazioni di Adobe Commerce sull&#39;infrastruttura cloud per utilizzare [Gestione configurazione](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md) (e si sposta la generazione di risorse statiche nella fase di compilazione per ridurre i tempi di inattività del sito Web durante la distribuzione), è possibile che si verifichi il seguente errore durante l&#39;esecuzione manuale del comando `setup:static-content:deploy`:

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
