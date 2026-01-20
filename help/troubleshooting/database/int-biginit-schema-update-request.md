---
title: Valore numerico del database Adobe Commerce non compreso nell’intervallo, da "INT" a "BIGINT"
description: Questo articolo fornisce soluzioni per i casi in cui non è possibile salvare un aggiornamento del prodotto, ad esempio una modifica del prezzo o l’eliminazione e la duplicazione di un prodotto.
exl-id: e2a00371-9032-4e81-b60e-5456ba35be94
feature: Services
role: Developer
source-git-commit: 5ca7a4400e62db2419b32a31a4f6cf04f5a82e35
workflow-type: tm+mt
source-wordcount: '577'
ht-degree: 0%

---

# Valore numerico del database Adobe Commerce non compreso nell&#39;intervallo, da `INT` a `BIGINT`

>[!WARNING]
>
>Prima di implementare la soluzione in questo articolo (`INT` in `BIGINT` aggiornamento schema) i commercianti devono sempre verificare che il campo che stanno per modificare NON presenti relazioni di chiave esterna con un&#39;altra tabella. Se il campo ha relazioni di chiave esterna con un&#39;altra tabella, si verificheranno problemi perché il campo correlato è ancora `INT`. Per verificarlo, è possibile utilizzare la query seguente. Questa query elenca le relazioni di chiave esterna disponibili nel database per il campo di tabella specificato:
>
```mysql
>SELECT 
>     TABLE_NAME,COLUMN_NAME,CONSTRAINT_NAME,REFERENCED_TABLE_NAME,REFERENCED_COLUMN_NAME
>FROM
>   INFORMATION_SCHEMA.KEY_COLUMN_USAGE
>WHERE
>     REFERENCED_TABLE_SCHEMA = '<database_name>' AND
>     REFERENCED_TABLE_NAME = '<table_name>' AND
>     REFERENCED_COLUMN_NAME = '<table_field>';
>```

## Prodotti e versioni interessati

* Adobe Commerce (tutti i metodi di distribuzione) tutte le [versioni supportate](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

Questo articolo fornisce soluzioni per i casi in cui non è possibile salvare un aggiornamento del prodotto, ad esempio una modifica del prezzo o l’eliminazione e la duplicazione di un prodotto.
È possibile che venga visualizzato il messaggio di errore *Impossibile salvare l&#39;elemento azionario. Riprova.* È possibile che la distribuzione non riesca dopo un aggiornamento del prodotto. È inoltre possibile che venga visualizzato il seguente messaggio di errore [!DNL MySQL] quando si esegue `php bin/magento setup:upgrade` (in Adobe Commerce sull&#39;infrastruttura cloud questo errore viene visualizzato nei registri di distribuzione):

```mysql
SQLSTATE[22003]: Numeric value out of range: 167 Out of range value for column 'value_id' at row 1, query was: INSERT INTO `catalog_product_entity_decimal` (`attribute_id`,`store_id`,`row_id`,`value`) VALUES (?, ?, ?, ?) ON DUPLICATE KEY UPDATE `attribute_id` = VALUES(`attribute_id`), `store_id` = VALUES(`store_id`), `row_id` = VALUES(`row_id`), `value` = VALUES(`value`)
```

Le soluzioni descritte nell’articolo sono:
* Aggiorna `[ AUTO_INCREMENT ]` al valore successivo dalla tabella oppure
* Aggiornamento schema da `INT` a `BIGINT`

La soluzione utilizzata dipende dalla causa del problema. Per isolare la causa, consulta i passaggi seguenti.

## Passaggi per verificare la causa


Controllare il valore massimo della chiave primaria eseguendo il comando seguente nel terminale: `SELECT MAX(value_id) FROM catalog_product_entity_int;`

Se `max(value_id)` è inferiore a `max int(11) [ 4294967296 ]` e `[ AUTO_INCREMENT ]` ha un valore maggiore o uguale a `max int(11) [ 4294967296 ]`, provare ad aggiornare [il valore `[ AUTO_INCREMENT ]` al valore successivo dalla tabella](#update-the-auto-increment-to-the-next-value-from-the-table). In caso contrario, considerare un aggiornamento dello schema da [`INT` a `BIGINT`](#int_to_bigint_schema_update).

## Aggiorna `AUTO_INCREMENT` al valore successivo dalla tabella {#update-the-auto-increment-to-the-next-value-from-the-table}

>[!WARNING]
>
>Eseguire un backup del database prima di modificare le tabelle. Impostare inoltre il sito in [modalità di manutenzione](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html#maintenance-mode). È inoltre consigliabile eseguire il comando di ottimizzazione [!DNL MySQL] sulle tabelle del database (solo nelle tabelle in cui sono state apportate modifiche) dopo aver apportato le modifiche.

>[!NOTE]
>
>Il sito deve essere in modalità manutenzione durante l’esecuzione del comando ottimizza su tabelle specifiche. In questo modo le tabelle vengono completamente ricreate e dopo l&#39;eliminazione dei dati dalle tabelle verrà liberato spazio.

Se il valore mostrato è inferiore a `max int(11) [ 4294967296 ]` come mostrato nell&#39;output del terminale di esempio seguente, una tabella `[ AUTO_INCREMENT ]` è stata modificata in un numero maggiore o uguale al valore `max [ int(11) ]`.

```mariadb
MariaDB [xxx]> SELECT MAX(value_id) FROM catalog_product_entity_int;
+---------------------+
| MAX(source_item_id) |
+---------------------+
|          4283174130 |
+---------------------+
```

Per verificare se ciò si è verificato, esegui il seguente comando nel terminale:

```
MariaDB [xxx]> show create table catalog_product_entity_int;

...
) ENGINE=InnoDB AUTO_INCREMENT=4294967297 DEFAULT CHARSET=utf8 COMMENT='Catalog Product Integer Attribute Backend Table';
```

Come è possibile vedere nell&#39;output dell&#39;esempio precedente, la tabella `[ AUTO_INCREMENT ]` è stata modificata in un numero maggiore di `max int(11) [ 4294967296 ]`. La soluzione consiste nell&#39;aggiornare `[ AUTO_INCREMENT]` al valore successivo dalla tabella:

```
ALTER TABLE catalog_product_entity_int AUTO_INCREMENT = 4283174131;
```

## Aggiornamento schema da `INT` a `BIGINT` {#int_to_bigint_schema_update}

Tuttavia, se durante l&#39;esecuzione della seguente query `SELECT MAX(value_id) FROM catalog_product_entity_int;` il valore visualizzato è superiore a `max int(11) [ 4294967296 ]`, provare a eseguire un aggiornamento dello schema da `INT` a `BIGINT`. Il tipo di dati `BIGINT` ha un intervallo di valori più ampio.

Per eseguire questa operazione:

1. Crea un modulo personalizzato nella directory *app/code/*.
1. Nel modulo personalizzato creare un *db_schema.xml*. In *db_schema.xml* verrà impostato il tipo di dati su `BIGINT`.
1. Aggiungere il contenuto seguente ed eseguire `bin/magento setup:upgrade` per applicare le modifiche precedenti alla tabella corrispondente.

```
<?xml version="1.0"?>
<schema xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Setup/Declaration/Schema/etc/schema.xsd">
    <table name="catalog_product_entity_int">
        <column xsi:type="bigint" name="value_id" unsigned="false" nullable="false" identity="true"
                comment="Value ID"/>
    </table>
</schema>
```


## Lettura correlata

* [Indicazioni generali [!DNL MySQL] ](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/database-server/mysql.html) nella Guida all&#39;installazione di Commerce
* [Best practice per il database di Adobe Commerce sull&#39;infrastruttura cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/best-practices/database/database-best-practices-for-magento-commerce-cloud.html) nella knowledge base per il supporto
* [Problemi di database più comuni in Adobe Commerce sull&#39;infrastruttura cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/best-practices/database/most-common-database-issues-in-magento-commerce-cloud.html) nella knowledge base di supporto
* [Best practice per la modifica delle tabelle del database](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) nel playbook di implementazione di Commerce
