---
title: Errore "Impossibile salvare la classe nella directory del codice"
description: Questo articolo descrive come risolvere il problema in cui il modo in cui hai specificato le dipendenze impedisce la generazione automatica immediata delle classi e viene visualizzato il messaggio di errore *"Class cannot be save in the generated/code directory"*.
exl-id: e2c00d4d-31c3-4446-a317-a8ac92c707d5
feature: Configuration
role: Developer
source-git-commit: 139c2836ba36686357c7a5458a36550c7b1273c1
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# Errore &quot;Impossibile salvare la classe nella directory del codice&quot;

In questo articolo viene descritto come risolvere il problema in cui il modo in cui sono state specificate le dipendenze impedisce la generazione automatica immediata delle classi e viene visualizzato il messaggio di errore *&quot;Impossibile salvare la classe nella directory generato/code&quot;*.

## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud 2.2.0 o versione successiva

## Problema

<u>Passaggi da riprodurre</u>

1. Nell’ambiente locale, scrivi una classe personalizzata con una dipendenza dalla classe generata automaticamente.
1. Esegui lo scenario in cui viene attivata la classe personalizzata e verificane il corretto funzionamento.
1. Apporta le modifiche all&#39;ambiente di integrazione. Questo attiverebbe il processo di distribuzione. Implementazione completata.
1. Nell&#39;[ambiente di integrazione](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27242), esegui lo scenario in cui viene attivata la classe personalizzata.

<u>Risultato previsto</u>

Tutto funziona correttamente, nello stesso modo in cui funziona nell’ambiente locale.

<u>Risultato effettivo</u>

Errore con il messaggio di errore che indica che la classe non può essere salvata nella directory `generated/code`.

## Causa

La causa del problema è che la classe sulla quale si ha la dipendenza non viene generata durante la distribuzione e non può essere generata in un secondo momento quando la classe viene attivata, perché la directory `generated/code` non è disponibile per la scrittura dopo il completamento della distribuzione.

Questo può accadere per due motivi principali:

* Caso 1: la classe con dipendenze su classi generate automaticamente si trova nel punto di ingresso (ad esempio `index.php` ), che non viene analizzato per individuare dipendenze durante la distribuzione.
* Caso 2: la dipendenza dalla classe generata automaticamente viene specificata direttamente (rispetto all&#39;utilizzo consigliato del costruttore per dichiarare la dipendenza).

## Soluzione

Una soluzione comune per entrambi i casi sarebbe la creazione di una fabbrica reale invece della classe generata automaticamente.

Oppure c&#39;è una soluzione particolare per ogni caso.

### Soluzione specifica per il caso 1

Spostare il codice di classe dal punto di ingresso a un modulo separato e quindi utilizzarlo nel punto di ingresso.

<u>Esempio</u>

Codice originale, ad esempio, `index2.php`:

```php
<?php
use YourVendor\SomeModule\Model\GeneratedFactory;

require realpath(__DIR__) . '/../app/bootstrap.php';
$bootstrap = \Magento\Framework\App\Bootstrap::create(BP, $_SERVER);

class SomeClass
{
    private $generatedFactory;

    public function __construct(GeneratedFactory $generatedFactory)
    {
        $this->generatedFactory = $generatedFactory;
    }

// Some code here...
}

$someObject = $bootstrap->getObjectManager()->create(SomeClass::class);

// There is some code that uses $someObject
```

Devi effettuare le seguenti operazioni:

1. Sposta la definizione della classe in `app/code/YourVendor/YourModule`:

   ```php
      <?php
       namespace YourVendor\YourModule;
       use YourVendor\YourModule\Model\GeneratedFactory;
       class YourClass
       {
           private $generatedFactory;
   
           public function __construct(GeneratedFactory $generatedFactory)
           {
               $this->generatedFactory = $generatedFactory;
           }
       // Some code here...
       }
   ```

1. Modificare il punto di ingresso `my_api/index.php` in modo che sia simile al seguente:

   ```php
     <?php
     use YourVendor\YourModule\YourClass;
         require realpath(__DIR__) . '/../app/bootstrap.php';
         $bootstrap = \Magento\Framework\App\Bootstrap::create(BP, $_SERVER);
         $someObject = $bootstrap->getObjectManager()->create(YourClass::class);
     // Some code using $someObject
   ```

### Soluzione specifica per il caso 2

Sposta la dichiarazione di dipendenza nel costruttore.

<u>Esempio</u>

Dichiarazione di classe originale:

```php
<?php
namespace YourVendor\YourModule;

use YourVendor\SomeModule\Model\GeneratedFactory;
use Magento\Framework\App\ObjectManager;

class YourClass
{
    private $generatedFactory;
    private $someParam;

    public function __construct($someParam)
    {
        $this--->someParam = $someParam;
        $this->generatedFactory = ObjectManager::getInstance()->get(GeneratedFactory::class);
    }

    // Some code here...
}
```

È necessario modificare il costruttore come segue:

```php
<?php
namespace YourVendor\YourModule;

use YourVendor\YourModule\Model\GeneratedFactory;
use Magento\Framework\App\ObjectManager;

class YourClass
{
    private $generatedFactory;
    private $someParam;

    public function __construct($someParam, GeneratedFactory $generatedFactory = null)
    {
        $this->someParam = $someParam;
        $this->generatedFactory = $generatedFactory ?: ObjectManager::getInstance()->get(GeneratedFactory::class);
    }

    // Some code here...
}
```

## Lettura correlata

* [Generazione del codice](https://developer.adobe.com/commerce/php/development/components/code-generation/) nella documentazione per gli sviluppatori.
