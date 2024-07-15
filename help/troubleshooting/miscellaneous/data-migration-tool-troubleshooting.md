---
title: Risoluzione dei problemi relativi allo strumento di migrazione dei dati
description: Questo articolo fornisce soluzioni per gli errori che possono verificarsi quando si esegue lo strumento di migrazione dati.
exl-id: 9beb31ae-ed3c-42e1-b0bf-33fb1c91e0ea
feature: Data Import/Export
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 0%

---

# Risoluzione dei problemi relativi allo strumento di migrazione dei dati

Questo articolo fornisce soluzioni per gli errori che possono verificarsi quando si esegue lo strumento di migrazione dati.

## Documenti/campi Source non mappati {#source-documents-fields-not-mapped}

### Messaggi di errore

* ```bash    Source documents are not mapped: <EXTENSION_TABLE>    ```
* ```bash    Source fields are not mapped. Document: <EXTENSION_TABLE>. Fields: <EXTENSION_FIELD>    ```

In rari casi, il messaggio potrebbe indicare

```bash
Destination documents
```

o

```bash
Destination fields
```

invece di quelli sorgente.

### Causa

Alcune entità Adobe Commerce versione 1 (nella maggior parte dei casi, provenienti dalle estensioni) non esistono nel database Adobe Commerce versione 2.

Questo messaggio viene visualizzato perché lo strumento di migrazione dati esegue test interni per verificare che le tabelle e i campi siano coerenti tra i database *source* (Adobe Commerce 1) e *destination* (Adobe Commerce 2).

### Soluzioni possibili

* Installa le estensioni Adobe Commerce 2 corrispondenti da [Commerce Marketplace](https://marketplace.magento.com/).     Se i dati in conflitto provengono da un’estensione che aggiunge elementi della struttura del database, la versione Adobe Commerce 2 della stessa estensione può aggiungere tali elementi al database di destinazione (Adobe Commerce 2), risolvendo così il problema.
* Utilizzare l&#39;argomento `-a` durante l&#39;esecuzione dello strumento per risolvere automaticamente gli errori e impedire l&#39;interruzione della migrazione.
* Configura lo strumento per ignorare i dati problematici.

Per ignorare le entità di database, aggiungere il tag `<ignore>` a un&#39;entità nel file `map.xml`, come segue:

```xml
...
    <source>
        <document_rules>
            ...
            <!-- Ignore `sales_flat_invoice_grid` table -->
            <ignore>
                <document>sales_flat_invoice_grid</document>
            </ignore>
            <!-- Ignore `address_id` field of `sales_flat_order_address` table -->
            <ignore>
                <field>sales_flat_order_address.address_id</field>
            </ignore>
            ...
        </document_rules>
    </source>
    ...
```

>[!WARNING]
>
>Prima di ignorare le entità tramite il file mappa o utilizzando l&#39;opzione `-a`, accertati di non aver bisogno dei dati interessati nell&#39;archivio di Adobe Commerce 2.

## Classe non mappata nel record {#class-does-not-exist-but-mentioned}

### Messaggio di errore

```bash
Class <extension/class_name> is not mapped in record <attribute_id=196>
```

### Causa

Impossibile trovare una classe da Adobe Commerce 1 codebase nella base di codice di Adobe Commerce 2 durante il [passaggio di migrazione EAV](https://devdocs.magento.com/guides/v2.3/migration/migration-tool-internal-spec.html#eav) nella documentazione per gli sviluppatori. Nella maggior parte dei casi, la classe mancante appartiene a un&#39;estensione [extension](https://glossary.magento.com/extension).

### Soluzioni possibili

* Installa l’estensione Adobe Commerce 2 corrispondente.
* Ignora l’attributo che causa il problema.    Per questo, aggiungere l&#39;attributo al gruppo `ignore` nel file `eav-attribute-groups.xml.dist`.
* Aggiungere il mapping di classe utilizzando il file `class-map.xml.dist`.

## Il vincolo di chiave esterna ha esito negativo

### Testo messaggio di errore

```bash
Foreign key <KEY_NAME> constraint fails on source database. Orphan records id: <id_1>, <id_2> from <child_table>.<field_id> has no referenced records in <parent_table>
```

### Causa

Record di database mancanti in `parent_table` a cui punta `field_id` di `child_table`.

### Soluzione possibile

Eliminare i record da `child_table`, se non sono necessari.

Per mantenere i record, disabilitare `Data Integrity Step` modificando `config.xml` dello strumento di migrazione dati.

## Duplicati nelle riscritture URL

```xml
There are duplicates in URL rewrites:
Request path: towel.html Store ID: 2 Target path: catalog/product/view/id/10
Request path: towel.html Store ID: 2 Target path: catalog/product/view/id/12
```

### Causa

`Target path` in una riscrittura URL deve essere specificato da una coppia univoca di `Request path` + `Store ID`. Questo errore segnala due voci che utilizzano la stessa coppia `Request path` + `Store ID` con due valori `Target path` diversi.

### Soluzione possibile

Abilita l&#39;opzione `auto_resolve_urlrewrite_duplicates` nel file `config.xml`.

Questa configurazione aggiunge una stringa hash ai record in conflitto di [URL](https://glossary.magento.com/url) riscrive e mostra il risultato della risoluzione nell&#39;interfaccia della riga di comando.

## Mancata corrispondenza di entità {#mismatch-of-entities}

### Messaggio di errore

```bash
Mismatch of entities in the document: <DOCUMENT> Source: <COUNT_ITEMS_IN_SOURCE_TABLE> Destination: <COUNT_ITEMS_IN_DESTINATION_TABLE>
```

### Causa

L&#39;errore si verifica durante il passaggio Controllo volume. Ciò significa che il conteggio dei record del database Adobe Commerce 2 del documento non è lo stesso di Adobe Commerce 1.

I record mancanti si verificano quando un cliente effettua un ordine durante la migrazione.

### Soluzione possibile

Eseguire lo strumento di migrazione dati in modalità `Delta` per trasferire le modifiche incrementali.

## Deltalog non è installato {#deltalog-is-not-installed}

### Messaggio di errore

```bash
Deltalog for <TABLE_NAME> is not installed
```

### Causa

Questo errore si verifica durante la [migrazione incrementale](https://devdocs.magento.com/guides/v2.3/migration/migration-migrate-delta.html) (nella documentazione per gli sviluppatori) delle modifiche ai dati. Ciò significa che non sono state trovate le tabelle di deltalog (con prefisso `m2_cl_*`) nel database di Adobe Commerce 1. Lo strumento installa queste tabelle durante la [migrazione dei dati](https://devdocs.magento.com/guides/v2.3/migration/migration-migrate-data.html) (nella documentazione per gli sviluppatori), nonché i trigger del database che tengono traccia delle modifiche e riempiono le tabelle del catalogo.

Uno dei motivi dell&#39;errore potrebbe essere che si sta tentando di eseguire la migrazione da una *copia* dell&#39;archivio Adobe Commerce 1 live, non dall&#39;archivio live stesso. Quando crei una copia da un archivio Adobe Commerce 1 live che non è mai stata migrata, la copia non contiene i trigger e le tabelle di dialogo aggiuntive necessarie per completare una migrazione delta, pertanto la migrazione non riesce. Lo strumento di migrazione dei dati NON effettua confronti tra il database di AC1 e AC2 per migrare le differenze. Per eseguire le migrazioni delta successive, lo strumento utilizza invece le tabelle triggers e deltalog installate durante la prima migrazione. In questo caso, la tua copia del database live di Adobe Commerce 1 non conterrà i trigger e le tabelle di deltalog utilizzati dallo strumento di migrazione dei dati per eseguire una migrazione.

### Soluzione possibile

Per risolvere i problemi di migrazione, è consigliabile eseguire il test del processo di migrazione da una copia del database Adobe Commerce 1. Dopo aver risolto i problemi sulla copia, riavvia il processo di migrazione dal database live Adobe Commerce 1. Ciò contribuirà a garantire un processo di migrazione agevole.
