---
title: Errori durante l'installazione dei dati di esempio facoltativi
description: In questo argomento vengono illustrate le soluzioni agli errori che possono verificarsi durante l'installazione di dati di esempio facoltativi.
exl-id: 14692e3a-188c-45f1-9df5-ac873cc9eff0
feature: Console, Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# Errori durante l&#39;installazione dei dati di esempio facoltativi

In questo argomento vengono illustrate le soluzioni agli errori che possono verificarsi durante l&#39;installazione di dati di esempio facoltativi.

## Sintomo (autorizzazioni del file system)

Errore nel registro della console durante l&#39;installazione dei dati di esempio tramite l&#39;Installazione guidata:

```php
Module 'Magento_CatalogRuleSampleData':
[ERROR] exception 'Magento\Framework\Exception\LocalizedException' with message 'Can't create directory /var/www/html/magento2/generated/code/Magento/CatalogRule/Model/.' in /var/www/html/magento2/lib/internal/Magento/Framework/Code/Generator.php:103

(more)

Next exception 'ReflectionException' with message 'Class Magento\CatalogRule\Model\RuleFactory does not exist' in /var/www/html/magento2/lib/internal/Magento/Framework/Code/Reader/ClassReader.php:29

(more)
```

Queste eccezioni sono il risultato delle impostazioni delle autorizzazioni del file system.

### Soluzione

[Imposta nuovamente la proprietà e le autorizzazioni del file system](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/file-system-permissions.html) come utente con privilegi `root`.

## Sintomo (modalità di produzione)

Se si è impostati per la [modalità di produzione](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html), l&#39;installazione dei dati di esempio non riesce se si utilizza il comando [magento sampledata:deploy](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/sample-data/composer-packages.html):

```php
PHP Fatal error: Uncaught TypeError: Argument 1 passed to Symfony\Component\Console\Input\ArrayInput::__construct() must be of the type array, object given, called in /<path>/vendor/magento/framework/ObjectManager/Factory/AbstractFactory.php on line 97 and defined in /<path>/vendor/symfony/console/Symfony/Component/Console/Input/ArrayInput.php:37
```

### Soluzione

Non installare dati di esempio in modalità di produzione. Passa alla modalità sviluppatore, cancella alcune directory `var` e riprova.

Immettere i seguenti comandi nell&#39;ordine indicato come [proprietario del file system Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/file-system/overview.html):

```php
cd <magento_root>
bin/magento deploy:mode:set developer
rm -rf generated/code/* generated/metadata/*
bin/magento sampledata:deploy
```

## Sintomo (sicurezza)

Durante l’installazione dei dati di esempio facoltativi, viene visualizzato un messaggio simile al seguente:

```php
PHP Fatal error: Call to undefined method Magento\Catalog\Model\Resource\Product\Interceptor::getWriteConnection() in /var/www/magento2/app/code/Magento/SampleData/Module/Catalog/Setup/Product/Gallery.php on line 144
```

### Soluzione

Durante l’installazione di dati di esempio, disabilita SELinux utilizzando una risorsa come:

* [www.ibm.com](https://www.ibm.com/docs/ja/ahts/4.0?topic=t-disabling-selinux)
* [Documentazione CentOS](https://docs.centos.org/en-US/docs/)

## Sintomo (sviluppo di branca)

Vengono visualizzati altri errori, ad esempio:

```php
[Magento\Setup\SampleDataException] Error during sample data installation: Class Magento\Sales\Model\Service\OrderFactory does not exist
```

### Soluzione

Si sono verificati problemi noti nell’utilizzo di dati di esempio con il ramo di sviluppo Adobe Commerce. Utilizza invece il ramo principale. È possibile passare al ramo principale come indicato di seguito:

```php
cd <magento_root>
git checkout master
git pull origin master
```

## Sintomo (max_execution_time)

L&#39;installazione si interrompe prima del completamento dell&#39;installazione dei dati di esempio. Di seguito è riportato un esempio:

```php
(more)

Module 'Magento_CustomerSampleData':
Installing data...
```

L&#39;installazione dei dati di esempio non viene completata.

Questo errore si verifica quando viene superato il tempo massimo di esecuzione configurato per gli script PHP. Poiché il caricamento dei dati di esempio può richiedere molto tempo, è possibile aumentarne il valore durante l&#39;installazione.

### Soluzione

In qualità di utente con privilegi di `root`, modificare `php.ini` per aumentare il valore di `max_execution_time` a 600 o più. (600 secondi sono 10 minuti. È possibile aumentare il valore a quello desiderato.) Ripristinare il valore precedente di `max_execution_time` dopo l&#39;installazione.

Se non si è sicuri della posizione di `php.ini`, immettere il comando seguente:

```php
php --ini
```

Il valore di `Loaded Configuration File` è `php.ini` da modificare.

>[!NOTE]
>
>Siamo consapevoli che questo articolo può ancora contenere termini software standard del settore che alcuni possono trovare razzisti, sessisti o oppressivi e che possono far sentire il lettore ferito, traumatizzato, o sgradito. Adobe sta lavorando per rimuovere questi termini dal nostro codice, dalla nostra documentazione e dalle esperienze utente.
