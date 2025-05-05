---
title: Impossibile eseguire l'installazione con nginx
description: Questo articolo fornisce una correzione per un’installazione di Adobe Commerce non riuscita quando si utilizza il server web nginx.
exl-id: 0af90c7e-0733-41c8-b217-9595b133fa95
feature: Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '87'
ht-degree: 0%

---

# Impossibile eseguire l&#39;installazione con nginx

Questo articolo fornisce una correzione per un’installazione di Adobe Commerce non riuscita quando si utilizza il server web nginx.

## Problema

Se si utilizza il server Web Inginx e si tenta di installare il software Adobe Commerce, a volte l&#39;installazione non riesce.

## Soluzione

È possibile confermare il problema con il seguente errore nella directory `var/report`:

```php
NOTE: You cannot install Adobe Commerce using the Setup Wizard because the Adobe Commerce setup directory cannot be accessed.
You can install Adobe Commerce using either the command line or you must restore access to the following directory: /var/www/html/setup
If you are using the sample nginx configuration, please go to http://ce.mtf03.bcn.magento.com/setup/";i:1;s:641:"#0 /var/www/html/lib/internal/Magento/Framework/App/Http.php(213): Magento\Framework\App\Http->redirectToSetup(Object(Magento\Framework\App\Bootstrap), Object(Exception))
```

### Soluzione alternativa

Installare il software Adobe Commerce utilizzando la [riga di comando](https://experienceleague.adobe.com/it/docs/commerce-operations/installation-guide/advanced).
