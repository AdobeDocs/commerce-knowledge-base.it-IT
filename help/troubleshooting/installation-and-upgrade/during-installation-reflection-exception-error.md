---
title: Durante l'installazione, errore di eccezione di riflessione
description: In questo articolo viene fornita una soluzione per l'errore Eccezione di riflessione durante l'installazione.
exl-id: aed5f297-1339-4171-9392-04b3f93277ee
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---

# Durante l&#39;installazione, errore di eccezione di riflessione

In questo articolo viene fornita una soluzione per l&#39;errore Eccezione di riflessione durante l&#39;installazione.

## Dettagli {#details}

Durante l’installazione viene visualizzato un messaggio simile al seguente:

```php
[ERROR] exception 'ReflectionException' with message 'Class Magento\Framework\StoreManagerInterface does not exist' in /<path>/lib/internal/Magento/Framework/Code/Reader/ClassReader.php
```

## Soluzione {#solution}

Cancella tutte le directory e i file in Adobe Commerce `var` e installare di nuovo il software Adobe Commerce.

Come [Proprietario file system Adobe Commerce](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/file-sys-perms-over.html) o come utente con `root` , immettere i seguenti comandi:

```bash
$ cd <your Magento install directory>/var
```

```bash
$ rm -rf var/cache/* di/* generation/* page_cache/*
```

### Redis {#redis}

Se si utilizza Redis e viene comunque visualizzato un errore, cancellare la cache Redis come segue:

```bash
$ redis-cli FLUSHALL
```
