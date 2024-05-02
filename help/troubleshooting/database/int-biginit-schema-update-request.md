---
title: Valore numerico del database Adobe Commerce non compreso nell’intervallo, da "INT" a "BIGINT"
description: Questo articolo fornisce soluzioni per i casi in cui non è possibile salvare un aggiornamento del prodotto, ad esempio una modifica del prezzo o l’eliminazione e la duplicazione di un prodotto.
exl-id: e2a00371-9032-4e81-b60e-5456ba35be94
feature: Services
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# valore numerico del database Adobe Commerce non compreso nell’intervallo valido, `INT` a `BIGINT`

>[!WARNING]
>
>Prima di implementare la soluzione in questo articolo (`INT` a `BIGINT` aggiornamento schema) i commercianti devono sempre verificare che il campo che intendono modificare NON presenti relazioni di chiave esterna con un’altra tabella. Se il campo ha relazioni di chiave esterna con un’altra tabella, si verificheranno dei problemi perché il campo correlato è ancora `INT`. Per verificarlo, è possibile utilizzare la query seguente. Questa query elenca le relazioni di chiave esterna disponibili nel database per il campo di tabella specificato:
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

* Adobe Commerce (tutti i metodi di distribuzione) tutto [versioni supportate](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

Questo articolo fornisce soluzioni per i casi in cui non è possibile salvare un aggiornamento del prodotto, ad esempio una modifica del prezzo o l’eliminazione e la duplicazione di un prodotto.
È possibile che venga visualizzato il messaggio di errore *Impossibile salvare l&#39;articolo azionario. Riprova.* Dopo un aggiornamento del prodotto, potrebbe non essere possibile eseguire la distribuzione. È inoltre possibile che venga visualizzato il seguente messaggio di errore MySQL quando si esegue `php bin/magento setup:upgrade` (in Adobe Commerce su infrastruttura cloud questo errore viene visualizzato nei registri di distribuzione):

```mysql
SQLSTATE[22003]: Numeric value out of range: 167 Out of range value for column 'value_id' at row 1, query was: INSERT INTO `catalog_product_entity_decimal` (`attribute_id`,`store_id`,`row_id`,`value`) VALUES (?, ?, ?, ?) ON DUPLICATE KEY UPDATE `attribute_id` = VALUES(`attribute_id`), `store_id` = VALUES(`store_id`), `row_id` = VALUES(`row_id`), `value` = VALUES(`value`)
```

Le soluzioni descritte nell’articolo sono:
* Aggiornare il `[ AUTO_INCREMENT ]` al valore successivo della tabella oppure
* `INT` a `BIGINT` aggiornamento schema

La soluzione utilizzata dipende dalla causa del problema. Per isolare la causa, consulta i passaggi seguenti.

## Passaggi per verificare la causa


Verifica il valore più alto della chiave primaria eseguendo il seguente comando nel terminale: `SELECT MAX(value_id) FROM catalog_product_entity_int;`

Se il `max(value_id)` è inferiore al valore `max int(11) [ 4294967296 ]`e `[ AUTO_INCREMENT ]` ha un valore maggiore o uguale a `max int(11) [ 4294967296 ]`, quindi considera [aggiornamento di `[ AUTO_INCREMENT ]` al valore successivo della tabella](#update-the-auto-increment-to-the-next-value-from-the-table). In caso contrario, considera [`INT` a `BIGINT` aggiornamento schema](#int_to_bigint_schema_update).

## Aggiornare il `AUTO_INCREMENT` al valore successivo della tabella {#update-the-auto-increment-to-the-next-value-from-the-table}

>[!WARNING]
>
>Eseguire un backup del database prima di modificare le tabelle. Inoltre, inserisci il sito [modalità di manutenzione](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html#maintenance-mode). Si consiglia inoltre di eseguire il comando di ottimizzazione MYSQL sulle tabelle del database (solo per le tabelle in cui sono state apportate modifiche) dopo aver apportato le modifiche.

>[!NOTE]
>
>Il sito deve essere in modalità manutenzione durante l’esecuzione del comando ottimizza su tabelle specifiche. In questo modo le tabelle vengono completamente ricreate e dopo l&#39;eliminazione dei dati dalle tabelle verrà liberato spazio.

Se il valore mostrato è inferiore a `max int(11) [ 4294967296 ]` come mostrato nell’esempio seguente, uscita terminale, rispetto a una tabella `[ AUTO_INCREMENT ]` è stato modificato in un numero maggiore o uguale al `max [ int(11) ]` valore.

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

Come puoi vedere nell’output dell’esempio precedente, la tabella `[ AUTO_INCREMENT ]` è stato modificato in un numero maggiore di `max int(11) [ 4294967296 ]`. La soluzione consiste nell&#39;aggiornare `[ AUTO_INCREMENT]` al valore successivo della tabella:

```
ALTER TABLE catalog_product_entity_int AUTO_INCREMENT = 4283174131;
```

## `INT` a `BIGINT` aggiornamento schema {#int_to_bigint_schema_update}

Tuttavia, se durante l’esecuzione della query seguente `SELECT MAX(value_id) FROM catalog_product_entity_int;` il valore mostrato è superiore a `max int(11) [ 4294967296 ]`  considerare l&#39;esecuzione di una `INT` a `BIGINT` aggiornamento dello schema. Tipo di dati `BIGINT` ha un intervallo di valori più ampio.

Per eseguire questa operazione:

1. Creare un modulo personalizzato all’interno del *app/code/* directory.
1. Nel modulo personalizzato, crea un’ *db_schema.xml*. In entrata *db_schema.xml* il tipo di dati verrà impostato su `BIGINT`.
1. Aggiungi il seguente contenuto e quindi esegui `bin/magento setup:upgrade` per applicare le modifiche precedenti alla tabella corrispondente.

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

* [Linee guida generali di MySQL](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/database-server/mysql.html) nella Commerce Installation Guide.
* [Il caricamento del database perde la connessione a MySQL](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/database-upload-loses-connection-to-mysql.html) nella nostra knowledge base di supporto.
* [Best practice per il database di Adobe Commerce sull’infrastruttura cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/best-practices/database/database-best-practices-for-magento-commerce-cloud.html) nella nostra knowledge base di supporto.
* [Problemi di database più comuni in Adobe Commerce sull’infrastruttura cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/best-practices/database/most-common-database-issues-in-magento-commerce-cloud.html) nella nostra knowledge base di supporto.
