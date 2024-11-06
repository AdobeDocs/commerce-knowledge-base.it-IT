---
title: Durante l'installazione, errore di eccezione di riflessione
description: In questo articolo viene fornita una soluzione per l'errore Eccezione di riflessione durante l'installazione.
exl-id: aed5f297-1339-4171-9392-04b3f93277ee
feature: Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

Cancellare tutte le directory e i file nella sottodirectory `var` di Adobe Commerce e installare nuovamente il software Adobe Commerce.

Come [proprietario del file system di Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/file-system/overview) o come utente con privilegi `root`, immetti i seguenti comandi:

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
