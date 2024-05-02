---
title: eseguire 'setup:static-content:deploy` deployed_version.txt issue
description: 'Questo articolo fornisce una correzione per "deployed_version.txt": errore non scrivibile durante l’esecuzione dell’installazione di:static-content:deploy` manualmente.'
exl-id: 88d8c126-349f-49cd-8f02-2a32e4994521
feature: Deploy, Page Content, SCD
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 0%

---

# eseguire `setup:static-content:deploy` deploy_version.txt problema

Questo articolo fornisce una correzione per `deployed_version.txt` non è scrivibile durante l&#39;esecuzione di `setup:static-content:deploy` manualmente.

## Problema

Se segui i consigli di Adobe Commerce sull’infrastruttura cloud da utilizzare [Gestione configurazione](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md) (e spostare la generazione di risorse statiche nella fase di build per ridurre i tempi di inattività del sito web durante la distribuzione), si potrebbe verificare il seguente errore durante l’esecuzione di `setup:static-content:deploy` comando manuale:

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

Se desideri comunque eseguire la distribuzione di contenuto statico, rimuovi i symlink nel `pub/static` ed eseguire la `setup:static-content:deploy` di nuovo il comando:

```
find pub/static/ -maxdepth 1 -type l -delete
```
