---
title: '''[!DNL B2B] L''installazione di 1.4.0 non riesce in Adobe Commerce 2.4.6-p1 on-premise'
description: Questo articolo fornisce una soluzione alternativa per il problema on-premise di Adobe Commerce 2.4.6-p1 in cui [!DNL B2B] l'installazione della versione 1.4.0 non riesce.
feature: Install, Upgrade, B2B
role: Developer
exl-id: 4a557c13-7ec2-4cfe-b86e-bb0d1a441658
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# [!DNL B2B] Installazione di 1.4.0 non riuscita in Adobe Commerce 2.4.6-p1 on-premise

Questo articolo fornisce una soluzione alternativa per il problema on-premise di Adobe Commerce 2.4.6-p1 in cui [!DNL B2B] l&#39;installazione della versione 1.4.0 non riesce.

## Prodotti e versioni interessati

* Adobe Commerce 2.4.6-p1 **on-premise**
* [!DNL B2B] versione 1.4.0

>[!NOTE]
>
>[!DNL B2B] la versione 1.4.0 viene installata correttamente il **Adobe Commerce Cloud 2.4.6-p1**.

## Problema

<u>Passaggi da riprodurre</u>:

1. Installa Adobe Commerce 2.4.6-p1.

   ```terminal
   m2install.sh -s composer --ee -v 2.4.6-p1
   ```

1. Prova a installare [!DNL B2B] versione 1.4.0.

   ```terminal
   composer require magento/extension-b2b:1.4.0
   ```

<u>Risultati previsti</u>:

[!DNL B2B] la versione 1.4.0 viene installata su Adobe Commerce 2.4.6-p1 correttamente.

<u>Risultati effettivi</u>:

L’installazione non riesce e viene visualizzato il seguente errore:

```terminal
Your requirements could not be resolved to an installable set of packages.

  Problem 1
    - Root composer.json requires magento/extension-b2b 1.4.0 -> satisfiable by magento/extension-b2b[1.4.0].
    - magento/extension-b2b 1.4.0 requires magento/security-package-b2b 1.0.4-beta1 -> found magento/security-package-b2b[1.0.4-beta1] but it does not match your minimum-stability.


Installation failed, reverting ./composer.json and ./composer.lock to their original content.
```

## Soluzione alternativa

Installazione o aggiornamento di [!DNL B2B] versione 1.4.0 su Adobe Commerce 2.4.6-p1 aggiungendo dipendenze manuali per [!DNL B2B] pacchetto di sicurezza con [tag di stabilità](https://getcomposer.org/doc/04-schema.md#package-links).

1. Dalla directory di installazione di Adobe Commerce, aggiorna `composer.json` con le dipendenze richieste:

   ```terminal
   composer require magento/module-re-captcha-company=1.0.3-beta1@beta magento/security-package-b2b=1.0.4-beta1@beta
   ```

   **Output comando:**

   ```terminal
   Running composer update magento/module-re-captcha-company magento/security-package-b2b
   Loading composer repositories with package information
   Updating dependencies
   Lock file operations: 2 installs, 0 updates, 0 removals
     - Locking magento/module-re-captcha-company (1.0.3-beta1)
     - Locking magento/security-package-b2b (1.0.4-beta1)
   Writing lock file
   Installing dependencies from lock file (including require-dev)
   Package operations: 2 installs, 0 updates, 0 removals
     - Downloading magento/module-re-captcha-company (1.0.3-beta1)
     - Installing magento/module-re-captcha-company (1.0.3-beta1): Extracting archive
     - Installing magento/security-package-b2b (1.0.4-beta1)
   1 package suggestions were added by new dependencies, use `composer suggest` to see details.
   Package sebastian/phpcpd is abandoned, you should avoid using it. No replacement was suggested.
   Generating autoload files
   132 packages you are using are looking for funding.
   Use the `composer fund` command to find out more!
   No security vulnerability advisories found
   ```

1. Aggiorna `composer.json` da aggiungere [!DNL B2B] versione 1.4.0.

   ```terminal
   composer require magento/extension-b2b=1.4.0
   ```

   **Output comando:**

   ```terminal
   ./composer.json has been updated
   Running composer update magento/extension-b2b
   Loading composer repositories with package information
   Updating dependencies
   ...
   Generating autoload files
   132 packages you are using are looking for funding.
   Use the `composer fund` command to find out more!
   No security vulnerability advisories found
   ```

1. Completare il processo di installazione o aggiornamento.

   * [Installa [!DNL B2B] sull’infrastruttura cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/b2b-module.html)
   * [Installazione on-premise](https://experienceleague.adobe.com/docs/commerce-admin/b2b/install.html)
