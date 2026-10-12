---
title: Il comando Composer install sostituisce il file .gitignore, Adobe Commerce
description: Questo articolo fornisce una soluzione per quando un file ".gitignore" tracciato viene sovrascritto dal compositore su Adobe Commerce sull’infrastruttura cloud 2.4.2-p1 e 2.3.7.
exl-id: b0604bae-d630-4292-88d7-6945db30fcf4
feature: Install, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%
---
# Il comando Composer install sostituisce il file .gitignore, Adobe Commerce

Questo articolo fornisce una soluzione per quando un file `.gitignore` tracciato viene sovrascritto dal compositore su Adobe Commerce su infrastruttura cloud 2.4.2-p1 e 2.3.7.

## Prodotti e versioni interessati

Adobe Commerce su infrastruttura cloud 2.4.2-p1 e 2.3.7.

## Problema

Il file `.gitignore` viene sovrascritto durante l&#39;esecuzione del comando di installazione del compositore.

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
   1. `git commit -m "Init"` # file inviati al repository
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

`.gitignore` non è sovrascritto dal compositore.

<u>Risultato effettivo</u>:

`.gitignore` viene sovrascritto da ogni esecuzione dell&#39;installazione del compositore.

## Soluzione

Per mantenere `.gitignore file` personalizzato, è necessario ignorarlo nella sezione `magento-deploy-ignore`.

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

* [Il file .gitignore tracciato è stato sovrascritto dal compositore!](https://github.com/magento/magento2/issues/32888) in Magento2 GitHub.
