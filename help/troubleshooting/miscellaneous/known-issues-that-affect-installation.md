---
title: Problemi noti che influiscono sull'installazione di xdebug
description: Questo articolo fornisce una soluzione per quando si verifica un errore di eccezione quando si utilizza l’estensione PHP opzionale "xdebug".
exl-id: 5090ea99-e0c3-436a-809b-109701740927
feature: Install
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 0%

---

# Problemi noti che influiscono sull&#39;installazione di xdebug

Questo articolo fornisce una soluzione per quando si verifica un errore di eccezione quando si utilizza l&#39;estensione PHP opzionale `xdebug`.

* Durante l&#39;installazione
* Accesso all’amministrazione di Commerce o alla vetrina dopo una corretta installazione

Eccezione di esempio:

```php
Fatal error: Maximum function nesting level of '100' reached, aborting!
```

Per risolvere questo problema, puoi:

* Disattiva il `xdebug` estensione.
* Imposta il valore di `xdebug.max_nesting_level` a un valore pari o superiore a 200. Per ulteriori informazioni, consulta [documentazione di xdebug](http://xdebug.org/docs/basic#max_nesting_level).

Dopo aver modificato la configurazione di o disabilitato `xdebug`, riavvia Apache:

* CentOS: `sudo service httpd restart`
* Ubuntu: `sudo service apache2 restart`
