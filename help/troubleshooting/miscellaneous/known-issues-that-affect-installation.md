---
title: Problemi noti che influiscono sull'installazione di xdebug
description: Questo articolo fornisce una soluzione per quando si verifica un errore di eccezione quando si utilizza l’estensione PHP opzionale "xdebug".
exl-id: 5090ea99-e0c3-436a-809b-109701740927
feature: Install
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '109'
ht-degree: 0%
---
# Problemi noti che influiscono sull&#39;installazione di xdebug

Questo articolo fornisce una soluzione per l&#39;errore di eccezione che si verifica quando si utilizza l&#39;estensione PHP opzionale `xdebug`.

* Durante l&#39;installazione
* Accesso all’amministrazione di Commerce o alla vetrina dopo una corretta installazione

Eccezione di esempio:

```php
Fatal error: Maximum function nesting level of '100' reached, aborting!
```

Per risolvere questo problema, puoi:

* Disattiva l&#39;estensione `xdebug`.
* Impostare il valore di `xdebug.max_nesting_level` su un valore pari o superiore a 200. Per ulteriori informazioni, vedere la [documentazione xdebug](http://xdebug.org/docs/basic#max_nesting_level).

Dopo aver modificato la configurazione di o disabilitato `xdebug`, riavviare Apache:

* CentOS: `sudo service httpd restart`
* Ubuntu: `sudo service apache2 restart`
