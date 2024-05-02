---
title: Redis unserialize error `setup:static-content:deploy`
description: Questo articolo fornisce una correzione per l’errore Redis unserialize durante l’esecuzione di `magento setup:static-content:deploy`.
exl-id: 4bc88933-3bf9-4742-b864-b82d3c1b07a9
feature: Cache, Deploy, Page Content, SCD, Services, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# Errore di annullamento serializzazione Redis `setup:static-content:deploy`

Questo articolo fornisce una correzione per l’errore Redis unserialize durante l’esecuzione di `magento setup:static-content:deploy`.

In esecuzione `magento setup:static-content:deploy` causa l’errore Redis:

```
[Exception]
Notice: unserialize(): Error at offset 0 of 1 bytes in
/var/www/domain.com/vendor/magento/module-config/App/Config/Type/System.php on line 214
```

Il problema è causato da processi di interferenza paralleli sulla connessione Redis.

Per risolvere, esegui `setup:static-content:deploy` in modalità thread singolo impostando la seguente variabile di ambiente:

```
STATIC_CONTENT_THREADS =1
```

oppure, esegui `setup:static-content:deploy` seguito dal comando `-j 1` (o `--jobs=1` ).

La disattivazione del multithreading rallenta il processo di distribuzione delle risorse statiche.

## Versioni interessate

* Adobe Commerce on-premise: 2.1.2 e successive
* Adobe Commerce su infrastruttura cloud 2.1.2 e versioni successive
* Redis, qualsiasi versione

## Problema

Esecuzione di `setup:static-content:deploy` Il comando causa l&#39;errore Redis:

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

Qui, un processo in `App/Config/Type/System.php` era prevista una risposta per `system_defaultweb`, ma ha ricevuto una risposta per `system_cache_exists` è stato fatto con un processo diverso. Vedi la spiegazione dettagliata in [Post di Jason Woods](https://github.com/magento/magento2/issues/9287#issuecomment-302362283).

## Soluzione

Disattiva parallelismo ed esegui `setup:static-content:deploy` in modalità thread singolo impostando la seguente variabile di ambiente:

```
STATIC_CONTENT_THREADS =1
```

Inoltre, è possibile eseguire `setup:static-content:deploy` seguito dal comando `-j 1` (o `--jobs=1`).

>[!NOTE]
>
>Nella modalità a thread singolo, il processo di distribuzione del contenuto statico potrebbe richiedere quattro volte più tempo.

## Ulteriori informazioni

Nella documentazione per gli sviluppatori:

* [Configurare Redis](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/redis/config-redis.html)
* [Aggiornamento della riga di comando](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html)
