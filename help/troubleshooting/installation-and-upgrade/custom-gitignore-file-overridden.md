---
title: Il comando Composer install sostituisce il file .gitignore, Adobe Commerce
description: Questo articolo fornisce una soluzione per quando un file ".gitignore" tracciato viene sovrascritto dal compositore su Adobe Commerce sull’infrastruttura cloud 2.4.2-p1 e 2.3.7.
exl-id: b0604bae-d630-4292-88d7-6945db30fcf4
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# Il comando Composer install sostituisce il file .gitignore, Adobe Commerce

Questo articolo fornisce una soluzione per quando un `.gitignore` il file viene sovrascritto da compositore su Adobe Commerce on cloud infrastructure 2.4.2-p1 e 2.3.7.

## Prodotti e versioni interessati

Adobe Commerce su infrastruttura cloud 2.4.2-p1 e 2.3.7.

## Problema

`.gitignore` sovrascrittura del file durante l&#39;esecuzione del comando compositore installa.

<u>Passaggi da riprodurre</u>:


1. Crea una directory vuota per il workspace.
1. Esegui questo comando nella directory radice:

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-community-edition:2.4.2-p1.
   ```

   \# o 2.3.7

1. Eseguire quindi i seguenti comandi:
   1. `echo "/this/line/should/stay" >> .gitignore`
   1. `git init`
   1. `git add * && git add .*`
   1. `git commit -m "Init"` N. file impegnato nell’archivio
   1. `rm -rf vendor/*`
   1. `composer install`
   1. `git diff`

      ```git
      diff --git a/.gitignore b/.gitignore
      index c144521..7092a56 100644
      --- a/.gitignore
      +++ b/.gitignore
      @@ -70,4 +70,3 @@ atlassian*
      /generated/*
      !/generated/.htaccess
      .DS_Store
      -/this/line/should/stay
      ```

<u>Risultato previsto</u>:

`.gitignore` non viene sovrascritto dal compositore.

<u>Risultato effettivo</u>:

`.gitignore` viene sovrascritto da ogni esecuzione di installazione del compositore.

## Soluzione

Per mantenere il tuo `.gitignore file` devi ignorarlo nella sezione `magento-deploy-ignore` sezione.

```git
{
...
"extra": {
    "magento-deploy-ignore": {
        "*": [
            "/.gitignore"
        ]
    }
    ...
}
```


## Lettura correlata

* [Il file .gitignore tracciato viene sovrascritto dal compositore.](https://github.com/magento/magento2/issues/32888) in GitHub Magento2.
