---
title: Bootstrap Adobe Commerce 2 in uno script sandbox
description: 'Per inizializzare un’applicazione Adobe Commerce 2 in uno script sandbox di esempio, esegui lo script seguente dalla directory principale di Adobe Commerce:'
exl-id: a6acb30a-5175-42c6-8de3-e80c9ae8dac1
source-git-commit: c1c2bd29e14f4cbfffb235801e95ec7cbb7c7a55
workflow-type: tm+mt
source-wordcount: '58'
ht-degree: 0%

---

# Bootstrap Adobe Commerce 2 in uno script sandbox

Per inizializzare un’applicazione Adobe Commerce 2 in uno script sandbox di esempio, esegui lo script seguente dalla directory principale di Adobe Commerce:

```php
<?php

error_reporting(E_ALL | E_STRICT);
ini_set('display_errors', 1);

require __DIR__ . '/app/bootstrap.php';
$bootstrap = \Magento\Framework\App\Bootstrap::create(BP, $_SERVER);
$objectManager = $bootstrap->getObjectManager();

//$model = $objectManager->get('Vendor\Module\Some\Model');
```
