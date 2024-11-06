---
title: Durante l'installazione viene visualizzato un errore irreversibile di PDO
description: In questo articolo viene fornita una correzione per un errore PDO irreversibile di eccezione durante l'installazione.
exl-id: d69908f0-71c9-48de-9369-6ada22f2b393
feature: Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '50'
ht-degree: 0%

---

# Durante l&#39;installazione viene visualizzato un errore irreversibile di PDO

In questo articolo viene fornita una correzione per un errore PDO irreversibile di eccezione durante l&#39;installazione.

## Problema

```php
PHP Fatal error:  Class 'PDO' not found in /var/www/html/magento2/setup/module/Magento/Setup/src/Module/Setup/ConnectionFactory.php on line 44
```

## Soluzione

Assicurati di installare tutte le [estensioni PHP richieste](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/php-settings).
