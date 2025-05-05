---
title: Eliminazione sicura dei file quando lo spazio su disco in Adobe Commerce sull’infrastruttura cloud è esaurito
description: Questo articolo fornisce una soluzione per i casi in cui si esaurisce lo spazio su disco ed è necessario rimuovere i file in modo sicuro. Prima di considerare questa azione, consulta [Gestire lo spazio su disco](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#no-space-left) nella documentazione per gli sviluppatori. Se i passaggi descritti in tale articolo non sono appropriati per te o non risolvono il problema, rivedi i passaggi descritti in questo articolo.
exl-id: 6b0a5c1a-8db4-49d7-a785-b4e0bbaea0df
feature: Cloud, Paas
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# Eliminazione sicura dei file quando lo spazio su disco in Adobe Commerce sull’infrastruttura cloud è esaurito

## Prodotti e versioni interessati

* Adobe Commerce sull’infrastruttura cloud 2.4.2 - 2.4.7
* Questo è specifico per i cluster Pro dedicati. Gli ambienti Starter e Integration sono a nodo singolo e non dispongono della directory `/data/exports`.

## Segni di spazio su disco insufficiente

I segnali che indicano che lo spazio su disco è insufficiente possono essere distribuzione bloccata, avvertenze sull&#39;intero disco e prestazioni insoddisfacenti.
Per visualizzare la quantità di spazio su disco utilizzata dal file system, eseguire il comando seguente in CLI/Terminal:

`df -h`


## Come eliminare in modo sicuro i file per aumentare lo spazio su disco

È possibile eliminare i file dai punti di montaggio dell&#39;applicazione, dal percorso `/app` o tramite `/mnt/shared`. Sono due modi diversi per accedere agli stessi file.

>[!WARNING]
>
>**Non modificare o eliminare mai il contenuto di`/data/exports`**.
>
>`/data/exports` è l&#39;archiviazione sottostante il file system condiviso ed è gestito da GlusterFS.
>
>Il file system contiene non solo il contenuto del file, ma anche metadati sullo stato del file system per consentire la sincronizzazione >tra i nodi del cluster. **La modifica o l&#39;eliminazione diretta dei file all&#39;interno di questo file system danneggerà il file system condiviso, richiedendo riparazioni estese o il ripristino dei dati.**

Per individuare i file più grandi che potrebbero essere candidati validi per la cancellazione, eseguire il comando seguente (nei progetti di grandi dimensioni o occupati può richiedere fino a un&#39;ora):

```bash
FS='/data/exports';NUMRESULTS=20;resize;clear; echo "Please find below the Largest Directories and Files:";date;df -h $FS; echo "Largest Directories:";nice -n 19 find /app/*/ -type d -ls 2>/dev/null| sort -rnk1| head -n $NUMRESULTS| awk '
{printf "%d MB %s\n", $1/1024,$2}
';echo "Largest Files:"; nice -n 19 find /app/*/ -type f -ls 2>/dev/null| sort -rnk7| head -n $NUMRESULTS|awk '
{printf "%d MB\t%s\n", ($7/1024)/1024,$NF}
'; echo "Please use the above information to clear any unwanted data from the server, it is important this is done as soon as possible to ensure your server stays functional.";
```

L’output del comando conterrà un elenco dei file e delle directory più grandi con le relative dimensioni specificate.

## Lettura correlata

Nella nostra knowledge base di supporto:

* [Aumento dello spazio su disco per l’ambiente di integrazione su Cloud](/help/how-to/general/increase-disk-space-for-integration-environment-on-cloud.md)
* [Spazio su disco insufficiente](/help/troubleshooting/miscellaneous/low-disk-space.md)

Nella documentazione per gli sviluppatori:

* [Gestione spazio su disco](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space)
