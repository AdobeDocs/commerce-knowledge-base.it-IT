---
title: Durante l'installazione viene visualizzato un errore irreversibile di PDO
description: In questo articolo viene fornita una correzione per un errore PDO irreversibile di eccezione durante l'installazione.
exl-id: d69908f0-71c9-48de-9369-6ada22f2b393
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
source-wordcount: '60'
ht-degree: 0%
---
# Durante l&#39;installazione viene visualizzato un errore irreversibile di PDO

In questo articolo viene fornita una correzione per un errore PDO irreversibile di eccezione durante l&#39;installazione.

## Problema

```php
PHP Fatal error:  Class 'PDO' not found in /var/www/html/magento2/setup/module/Magento/Setup/src/Module/Setup/ConnectionFactory.php on line 44
```

## Soluzione

Assicurati di installare tutte le [estensioni PHP richieste](https://experienceleague.adobe.com/it/docs/commerce-operations/installation-guide/prerequisites/php-settings).
