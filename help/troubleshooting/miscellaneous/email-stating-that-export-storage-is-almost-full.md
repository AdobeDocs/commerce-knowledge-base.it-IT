---
title: E-mail che indica che lo spazio di archiviazione per le esportazioni è quasi pieno
description: Questo articolo fornisce una soluzione al problema in cui si riceve un messaggio e-mail che informa che lo spazio di archiviazione per le esportazioni è quasi pieno.
feature: Cloud, Storage, Media
role: Developer
exl-id: 7dae295c-919c-46c5-bf63-7d3467c2e07f
source-git-commit: 11cf981c7ebe813219a0cd311632eafce086bbf6
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# E-mail che indica che l’archiviazione delle esportazioni è quasi piena

Questo articolo fornisce una soluzione al problema in cui si riceve un messaggio e-mail che informa che lo spazio di archiviazione per le esportazioni è quasi pieno.

## Prodotti e versioni interessati

Adobe Commerce su infrastruttura cloud (tutte le versioni)

## Problema

Hai ricevuto un&#39;e-mail con il seguente contenuto ma non riesci a individuare la cartella *exports*:

*Il monitoraggio ha rilevato che l&#39;archivio &quot;esportazioni&quot; nel cluster XXX è pieno all&#39;incirca all&#39;85%.*
*Se necessario, controllare l&#39;utilizzo, eseguire una pulizia o richiedere un upsize.*
*Si noti inoltre che verrà eseguito automaticamente un upsize quando l&#39;archiviazione raggiunge il livello di soglia critica.*

## Causa

L&#39;avviso fa riferimento al file system di archiviazione delle esportazioni, ovvero il volume del disco in cui vengono memorizzati i supporti e altri dati di file. Questo file system viene in genere montato su `/data/exports`. L&#39;avviso non indica la presenza di una singola directory denominata letteralmente exports.

Per confermare a cosa si riferisce l’avviso, controlla l’utilizzo dell’archiviazione per le esportazioni:

* Eseguire `df -h | grep exports` e viene visualizzato il seguente output di esempio:

  ```
  /dev/nvme1n1 50G 38G 12G 77% /data/exports
  tmpfs         7.7G 4.0K 7.7G  1% /data/exports/shared
  ```

* In questo esempio, `/data/exports` è il file system di esportazione principale:

   * 50 GB in totale
   * 38 GB utilizzati
   * 12 GB disponibili (77% di utilizzo)

* `/data/exports/shared` è un mount `tmpfs` (in memoria) utilizzato per i dati condivisi e non contribuisce in modo significativo alla pressione del disco.

Ciò conferma che l&#39;avviso viene attivato dall&#39;utilizzo complessivo del disco di `/data/exports`, non da una singola cartella denominata exports.

Se `/data/exports` mostra un utilizzo elevato, le directory di grandi dimensioni in questo file system, ad esempio pub/supporti o altri percorsi di file personalizzati, sono in genere responsabili di un maggiore utilizzo.

## Soluzione

Segui questi passaggi per rivedere, pulire e convalidare l’utilizzo dello storage per le esportazioni.

1. Eseguire il comando `df -h | grep exports` per verificare l&#39;utilizzo corrente del file system di archiviazione delle esportazioni. Rivedi la colonna **Use%** per `/data/exports`:

   * Se l&#39;utilizzo è del 70-85%, avvia la pianificazione della pulizia.
   * Se l’utilizzo è superiore al 90%, intervieni immediatamente per evitare errori di scrittura o un impatto sul servizio.

1. Identificare le directory che occupano molto spazio su disco in `/data/exports` eseguendo:

   ```bash
   du -sh /data/exports/* 2>/dev/null
   ```

   I percorsi tipici in cui è probabile che l&#39;archiviazione dei file venga riempita sono `pub/media/catalog/product/cache` o `var/log` cartelle.

1. Pulizia dei file in base all&#39;ambiente:

   * Rimuovi prima i file di esportazione, i registri o i dati temporanei obsoleti o inutilizzati.
   * In ambienti non di produzione, in genere è possibile rimuovere i supporti di test o gli artefatti obsoleti in modo più aggressivo.
   * Negli ambienti di produzione, coordina con il tuo team prima di eliminare qualsiasi file multimediale o di importanza critica per l’azienda.

1. Dopo la pulizia, eseguire il comando seguente `df -h | grep exports` per confermare che il valore **Use%** per `/data/exports` è stato ridotto a un livello operativo sicuro.

## Lettura correlata

[Controlla i cluster dedicati](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#check-dedicated-clusters) nella knowledge base di supporto.
