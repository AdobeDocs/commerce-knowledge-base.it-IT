---
title: Come aggiungere un nuovo paese ad Adobe Commerce
description: Questo articolo spiega come aggiungere un paese che non è presente in Adobe Commerce e nella Libreria delle impostazioni internazionali di Zend. Questo richiede modifiche al codice e al database che costituiscono personalizzazioni del cliente in base ai termini del contratto applicabili. I materiali di esempio inclusi in questo articolo vengono forniti "COSÌ COM’È" senza alcuna garanzia. Né l’Adobe né alcun soggetto affiliato è obbligato a mantenere, correggere, aggiornare, modificare, modificare o altrimenti supportare tali materiali. Qui descriveremo i principi di base di ciò che è necessario fare per raggiungere questo obiettivo.
exl-id: af499add-4966-4a3a-972a-62a34c169a1b
feature: Build, Cache
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '1105'
ht-degree: 0%

---

# Come aggiungere un nuovo paese ad Adobe Commerce

Questo articolo spiega come aggiungere un paese che non è presente in Adobe Commerce e nella Libreria delle impostazioni internazionali di Zend. Questo richiede modifiche al codice e al database che costituiscono personalizzazioni del cliente in base ai termini del contratto applicabili. I materiali di esempio inclusi in questo articolo vengono forniti &quot;COSÌ COM’È&quot; senza alcuna garanzia. Né l’Adobe né alcun soggetto affiliato è obbligato a mantenere, correggere, aggiornare, modificare, modificare o altrimenti supportare tali materiali. Qui descriveremo i principi di base di ciò che è necessario fare per raggiungere questo obiettivo.

In questo esempio, creiamo un nuovo modulo Adobe Commerce con una patch di dati che viene applicata al momento dell’installazione o del processo di aggiornamento di Adobe Commerce e aggiunge ad Adobe Commerce un Paese astratto con il codice paese XX. La directory [Adobe Commerce](https://developer.adobe.com/commerce/php/module-reference/module-directory/) crea un elenco dei paesi iniziale e quindi utilizza le patch di installazione per aggiungere territori all&#39;elenco. Questo articolo spiega come creare un nuovo modulo che aggiungerà un nuovo paese all’elenco. È possibile consultare il codice del modulo Adobe Commerce Directory esistente come riferimento. Questo perché il modulo di esempio seguente continua il processo del modulo Directory di creazione di un elenco di paesi e aree geografiche e riutilizza parti del codice delle patch di installazione del modulo di Adobe Commerce Directory.

## Documentazione consigliata

Per crearne uno nuovo, è necessario avere familiarità con lo sviluppo del modulo Adobe Commerce.

Prima di creare un nuovo modulo, consulta i seguenti argomenti nella documentazione per gli sviluppatori:

* [Guida per gli sviluppatori PHP](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/bk-extension-dev-guide.html)
* [Panoramica modulo](https://devdocs.magento.com/guides/v2.4/architecture/archi_perspectives/components/modules/mod_intro.html)
* [Crea un nuovo modulo](https://devdocs.magento.com/videos/fundamentals/create-a-new-module/)
* [File di configurazione modulo](https://devdocs.magento.com/guides/v2.4/config-guide/config/config-files.html)

## Informazioni richieste

In Adobe Commerce, un nuovo paese deve avere un nome univoco, un ID paese, codici ISO2 e ISO3.

## Struttura del modulo

In questo esempio verrà creato un nuovo modulo denominato \`ExtraCountries\` con la seguente struttura di directory:

Per ulteriori informazioni sulla struttura del modulo, consulta [Panoramica del modulo](https://devdocs.magento.com/guides/v2.4/architecture/archi_perspectives/components/modules/mod_intro.html) nella documentazione per gli sviluppatori.

<pre><ExtraCountries>
 |
 <etc>
 | |
 | config.xml
 | di.xml
 | module.xml
 |
 <Plugin>
 | |
 | <Framework>
 |   |
 |   <Locale>
 |     |
 |     TranslatedListsPlugin.php
 |
 <Setup>
 | |
 | <Patch>
 |   |
 |   <Data>
 |     |
 |     AddDataForAbstractCountry.php
 |
 compositore.json
 registration.php</pre>

>[!NOTE]
>
>Ogni sezione dell’intestazione di questo articolo descrive i file della sezione della struttura del modulo.

## ExtraCountries/etc/config.xml

In questo file XML viene definita una nuova configurazione del modulo. È possibile modificare le configurazioni e i tag riportati di seguito per modificare le nuove impostazioni predefinite del paese.

* `allow` - Per aggiungere il nuovo paese all&#39;elenco &quot;Paesi consentiti&quot; per impostazione predefinita, aggiungi il nuovo codice paese alla fine del contenuto del tag `allow`. I codici paese sono separati da virgola. Tieni presente che questo tag sovrascriverà i dati del file di configurazione del modulo `Directory` *(Directory/etc/config.xml)* `allow` tag. Per questo motivo qui vengono ripetuti tutti i codici e viene aggiunto il nuovo.
* `optional_zip_countries` - Se il codice postale del nuovo paese aggiunto deve essere facoltativo, aggiungi il codice del paese alla fine del contenuto del tag `optional_zip_countries`. I codici paese sono separati da virgola. Tieni presente che questo tag sovrascriverà i dati del file di configurazione del modulo `Directory` *(Directory/etc/config.xml)* `optional_zip_countries` tag. Per questo motivo qui vengono ripetuti tutti i codici e viene aggiunto il nuovo.
* `eu_countries` - Se per impostazione predefinita il nuovo paese aggiunto deve far parte dell&#39;elenco dei paesi dell&#39;Unione europea, aggiungi il codice del paese alla fine del contenuto del tag `eu_countries`. I codici paese sono separati da virgola. Tieni presente che questo tag sovrascriverà i dati del file di configurazione del modulo `Store` *(\_Store/etc/config.xml\_)* `eu_countries` tag. Per questo motivo qui vengono ripetuti tutti i codici e ne viene aggiunto uno nuovo.
* `config.xml` esempio di file

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Store:etc/config.xsd">
    <default>
        <general>
            <country>
                <!-- append a new country codes to the end of this list -->
                <allow>AF,AL,DZ,AS,AD,AO,AI,AQ,AG,AR,AM,AW,AU,AT,AX,AZ,BS,BH,BD,BB,BY,BE,BZ,BJ,BM,BL,BT,BO,BQ,BA,BW,BV,BR,IO,VG,BN,BG,BF,BI,KH,CM,CA,CD,CV,KY,CF,TD,CL,CN,CX,CW,CC,CO,KM,CG,CK,CR,HR,CU,CY,CZ,DK,DJ,DM,DO,EC,EG,SV,GQ,ER,EE,ET,FK,FO,FJ,FI,FR,GF,PF,TF,GA,GM,GE,DE,GG,GH,GI,GR,GL,GD,GP,GU,GT,GN,GW,GY,HT,HM,HN,HK,HU,IS,IM,IN,ID,IR,IQ,IE,IL,IT,CI,JE,JM,JP,JO,KZ,KE,KI,KW,KG,LA,LV,LB,LS,LR,LY,LI,LT,LU,ME,MF,MO,MK,MG,MW,MY,MV,ML,MT,MH,MQ,MR,MU,YT,FX,MX,FM,MD,MC,MN,MS,MA,MZ,MM,NA,NR,NP,NL,AN,NC,NZ,NI,NE,NG,NU,NF,KP,MP,NO,OM,PK,PW,PA,PG,PY,PE,PH,PN,PL,PS,PT,PR,QA,RE,RO,RS,RU,RW,SH,KN,LC,PM,VC,WS,SM,ST,SA,SN,SC,SL,SG,SK,SI,SB,SO,ZA,GS,KR,ES,LK,SD,SR,SJ,SZ,SE,CH,SX,SY,TL,TW,TJ,TZ,TH,TG,TK,TO,TT,TN,TR,TM,TC,TV,VI,UG,UA,AE,GB,US,UM,UY,UZ,VU,VA,VE,VN,WF,EH,XK,YE,ZM,ZW,XX</allow>
​
                <!-- if added countries need to belong to the European Union Countries list by default, append their codes to the end of this list -->
                <eu_countries>AT,BE,BG,CY,CZ,DK,EE,FI,FR,DE,GR,HR,HU,IE,IT,LV,LT,LU,MT,NL,PL,PT,RO,SK,SI,ES,SE,GB,XX</eu_countries>
​
                <!-- if added countries are not require zip code, append it's code to the end of this list -->
                <optional_zip_countries>HK,IE,MO,PA,GB,XX</optional_zip_countries>
            </country>
        </general>
    </default>
</config>
```

Per ulteriori informazioni sui file di configurazione del modulo, consulta [Guida per gli sviluppatori PHP > Definire i file di configurazione](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/required-configuration-files.html) nella documentazione per gli sviluppatori.

Queste modifiche sono facoltative e influiranno solo sull’appartenenza predefinita del nuovo paese agli elenchi &quot;Paesi consentiti&quot;, &quot;CAP è facoltativo per&quot; e &quot;Paesi dell’Unione europea&quot;. Se questo file viene ignorato dalla struttura del modulo, verrà comunque aggiunto un nuovo paese, ma dovrà essere configurato manualmente nella pagina delle impostazioni **Admin** > **Stores** > *Settings* > **Configuration** > **General** > **Country Options**.

### ExtraCountries/etc/di.xml

Il file `di.xml` configura le dipendenze inserite dal gestore oggetti. Per ulteriori dettagli su `di.xml`, consulta la <a>Guida per gli sviluppatori PHP > Il di.xml</a> nella documentazione per gli sviluppatori.

Nel nostro esempio, dobbiamo registrare un `_TranslatedListsPlugin_` che tradurrà i codici paese appena introdotti in nomi di paese completi, se i codici non sono presenti nei dati di localizzazione della Libreria Zend Locale.

`di.xml` esempio

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
    <type name="Magento\Framework\Locale\TranslatedLists">
        <plugin name="Magento_Directory" type="VendorName\ExtraCountries\Plugin\Framework\Locale\TranslatedListsPlugin"/>
    </type>
</config>
```

### ExtraCountries/etc/module.xml

Nel file di registrazione del modulo è necessario specificare la dipendenza per il modulo &quot;Adobe Commerce Directory&quot;, assicurandosi che il modulo &quot;Extra Countries&quot; venga registrato ed eseguito dopo il modulo Directory.

Per ulteriori informazioni sulle dipendenze dei moduli, consulta [Gestione delle dipendenze dei moduli](https://devdocs.magento.com/guides/v2.4/architecture/archi_perspectives/components/modules/mod_depend.html#managing-module-dependencies) nella documentazione per gli sviluppatori.

`module.xml` esempio

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Module/etc/module.xsd">
    <module name="VendorName_ExtraCountries" >
        <sequence>
            <module name="Magento_Directory"/>
        </sequence>
    </module>
</config>
```

### ExtraCountries/Plugin/Framework/Locale/TranslatedListsPlugin.php

Nel metodo del plug-in `aroundGetCountryTranslation()` è necessario tradurre un codice paese in un nome paese completo. Questo passaggio è obbligatorio per i paesi a cui non è associato un nome completo con un nuovo codice paese nella libreria locale di Zend.

```php
<?php
namespace VendorName\ExtraCountries\Plugin\Framework\Locale;
​
use Magento\Framework\Locale\ListsInterface;
​
/**
 * Plugin to add full names of added countries that are not included in Zend Locale Data
 */
class TranslatedListsPlugin
{
    /**
     * Get the full name of added countries
     *
     * Since the locale data for the added country may not be present in the Zend Locale Library,
     * we need to provide full country name matching the added code
     *
     * @param ListsInterface $subject
     * @param callable $proceed
     * @param $value
     * @param null $locale
     * @return string
     */
    public function aroundGetCountryTranslation(
        ListsInterface $subject,
        callable $proceed,
        $value,
        $locale = null
    )
    {
        if ($value == 'XX') {
            return 'Abstract Country';
        }
​
        return $proceed($value, $locale);
    }
}
```

### ExtraCountries/Setup/Patch/Data/AddDataForAbstractCountry.php

Questa patch dati verrà eseguita durante il processo di installazione/aggiornamento di Adobe Commerce e aggiungerà un nuovo record del paese al database.

Per ulteriori informazioni sulle patch di dati, consulta [Sviluppare patch di dati e schemi](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/declarative-schema/data-patches.html) nella documentazione per gli sviluppatori.

Nell&#39;esempio seguente è possibile vedere che l&#39;array `$data` del metodo `apply()` contiene i codici Country ID, ISO2 e ISO3 per il nuovo paese e che questi dati vengono inseriti nel database.

```php
<?php
namespace Magento\ExtraCountries\Setup\Patch\Data;
​
use Magento\Framework\Setup\ModuleDataSetupInterface;
use Magento\Framework\Setup\Patch\DataPatchInterface;
use Magento\Framework\Setup\Patch\PatchVersionInterface;
​
/**
 * Add Abstract Country data to the country list
 *
 * @package Magento\ExtraCountries\Setup\Patch
 */
class AddDataForAbstractCountry implements DataPatchInterface, PatchVersionInterface
{
    /**
     * @var ModuleDataSetupInterface
     */
    private $moduleDataSetup;
​
    /**
     * @param ModuleDataSetupInterface $moduleDataSetup
     */
    public function __construct(
        ModuleDataSetupInterface $moduleDataSetup
    ) {
        $this->moduleDataSetup = $moduleDataSetup;
    }
​
    /**
     * @inheritdoc
     */
    public function apply()
    {
        /**
         * Fill table directory/country
         */
        $data = [
            ['XX', 'XX', 'XX']
        ];
​
        $columns = ['country_id', 'iso2_code', 'iso3_code'];
        $this->moduleDataSetup->getConnection()->insertArray(
            $this->moduleDataSetup->getTable('directory_country'),
            $columns,
            $data
        );
    }
​
    /**
     * @inheritdoc
     */
    public static function getDependencies()
    {
        return [];
    }
​
    /**
     * @inheritdoc
     */
    public static function getVersion()
    {
        return '0.0.1';
    }
​
    /**
     * @inheritdoc
     */
    public function getAliases()
    {
        return [];
    }
}
```

### ExtraCountries/registration.php

Questo è un esempio del file registration.php. Per ulteriori informazioni sulla registrazione del modulo, consulta [Guida per gli sviluppatori PHP > Registra il componente](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/component-registration.html) nella documentazione per gli sviluppatori.

```php
<?php
use Magento\Framework\Component\ComponentRegistrar;
​
ComponentRegistrar::register(ComponentRegistrar::MODULE, 'VendorName_ExtraCountries', __DIR__);
```

### ExtraCountries/composer.json

Questo è un esempio del file compositore.json.

Per ulteriori informazioni su compositore.json, consulta la [Guida per gli sviluppatori PHP > Il file compositore.json](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/composer-integration.html) nella documentazione per gli sviluppatori.

```json
{
    "name": "vendor_name/module-extra-countries",
    "description": "A module that adds extra countries to magento directory",
    "type": "magento2-module",
    "license": [
    ],
    "require": {
        "php": "~7.3.0||~7.4.0",
        "lib-libxml": "*",
        "magento/framework": "*",
        "magento/module-directory": "*"
    },
    "autoload": {
        "files": [
            "registration.php"
        ],
        "psr-4": {
            "VendorName\\ExtraCountries\\": ""
        }
    },
    "config": {
        "sort-packages": true
    }
}
```

## Installazione del modulo

Per informazioni su come installare il modulo, consulta [Percorsi del modulo](https://devdocs.magento.com/guides/v2.4/architecture/archi_perspectives/components/modules/mod_intro.html#module-locations) nella documentazione per gli sviluppatori.

Una volta che la directory del modulo è posizionata nella posizione corretta, eseguire `bin/magento setup:upgrade` per applicare le patch di dati e registrare il plug-in di traduzione.

Per il corretto funzionamento delle nuove modifiche, potrebbe essere necessario pulire la cache del browser.
