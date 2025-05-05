---
title: 'Redis: errore di annullamento della serializzazione "setup:static-content:deploy"'
description: Questo articolo fornisce una correzione per l’errore di annullamento della serializzazione Redis durante l’esecuzione di "magento setup:static-content:deploy".
exl-id: 4bc88933-3bf9-4742-b864-b82d3c1b07a9
feature: Cache, Deploy, Page Content, SCD, Services, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# Redis: errore di annullamento della serializzazione `setup:static-content:deploy`

Questo articolo fornisce una correzione per l&#39;errore di annullamento della serializzazione Redis durante l&#39;esecuzione di `magento setup:static-content:deploy`.

L&#39;esecuzione di `magento setup:static-content:deploy` causa l&#39;errore Redis:

```
[Exception]
Notice: unserialize(): Error at offset 0 of 1 bytes in
/var/www/domain.com/vendor/magento/module-config/App/Config/Type/System.php on line 214
```

Il problema è causato da processi di interferenza paralleli sulla connessione Redis.

Per risolvere il problema, eseguire `setup:static-content:deploy` in modalità thread singolo impostando la seguente variabile di ambiente:

```
STATIC_CONTENT_THREADS =1
```

in alternativa, eseguire il comando `setup:static-content:deploy` seguito dall&#39;argomento `-j 1` (o `--jobs=1` ).

La disattivazione del multithreading rallenta il processo di distribuzione delle risorse statiche.

## Versioni interessate

* Adobe Commerce on-premise: 2.1.2 e successive
* Adobe Commerce su infrastruttura cloud 2.1.2 e versioni successive
* Redis, qualsiasi versione

## Problema

L&#39;esecuzione del comando `setup:static-content:deploy` causa l&#39;errore Redis:

```php
)
[2017-06-02 19:57:59] Command:php ./bin/magento setup:static-content:deploy --jobs=3  en_US

[Exception]

Notice: unserialize(): Error at offset 0 of 1 bytes in /app/<domain>/vendor/magento/module-config/App/Config/Type/System.php
on line 214

.....

[CredisException]
read error on connection

[RedisException]
read error on connection

.....

[Exception]

Notice: unserialize(): Error at offset 0 of 1 bytes in /app/<domain>/vendor/magento/module-config/App/Config/Type/System.php
on line 214

.....

[RuntimeException]
Command php ./bin/magento setup:static-content:deploy --jobs=3  en_US  returned code 3
```

## Causa

Il problema è causato da processi di interferenza paralleli sulla connessione Redis.

In questo caso, un processo in `App/Config/Type/System.php` stava aspettando una risposta per `system_defaultweb`, ma ha ricevuto una risposta per `system_cache_exists` che è stata eseguita da un processo diverso. Vedi la spiegazione dettagliata nel [post di Jason Woods](https://github.com/magento/magento2/issues/9287#issuecomment-302362283).

## Soluzione

Disattivare il parallelismo ed eseguire `setup:static-content:deploy` in modalità thread singolo impostando la seguente variabile di ambiente:

```
STATIC_CONTENT_THREADS =1
```

È inoltre possibile eseguire il comando `setup:static-content:deploy` seguito dall&#39;argomento `-j 1` (o `--jobs=1`).

>[!NOTE]
>
>Nella modalità a thread singolo, il processo di distribuzione del contenuto statico potrebbe richiedere quattro volte più tempo.

## Ulteriori informazioni

Nella documentazione per gli sviluppatori:

* [Configura Redis](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/redis/config-redis.html?lang=it)
* [Aggiornamento riga di comando](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html?lang=it)
