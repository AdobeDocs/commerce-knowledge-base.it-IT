---
title: E-mail che indica che lo spazio di archiviazione per le esportazioni è quasi pieno
description: Questo articolo fornisce una soluzione al problema in cui si riceve un messaggio e-mail che informa che lo spazio di archiviazione per le esportazioni è quasi pieno.
feature: Cloud, Storage, Media
role: Developer
exl-id: 7dae295c-919c-46c5-bf63-7d3467c2e07f
source-git-commit: 89f985b832545f1fbccf94aac1d60f1e767b5bc4
workflow-type: tm+mt
source-wordcount: '277'
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

L&#39;e-mail fa riferimento all&#39;archivio **exports**, che corrisponde alla quantità di disco allocata ai file/supporti e non a una cartella specifica denominata *exports*.

## Soluzione

È necessario verificare l’utilizzo dei file nell’ambiente. Esegui questo comando per ottenere l’utilizzo esistente:

`df -h |grep data`

I percorsi tipici in cui è probabile che l&#39;archiviazione dei file venga riempita sono le cartelle *pub/media/catalog/product/cache* o *var/log*. Per determinare lo spazio su disco utilizzato dai file, eseguire questo comando con il percorso appropriato */path/to/folder*:

`du -shc` */path/to/folder*

Se l&#39;utilizzo del disco multimediale costituisce una percentuale elevata dello spazio totale su disco, è consigliabile abilitare [Fastly Deep Image Optimization](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization#deep-image-optimization), quindi eliminare manualmente i file nella cartella *pub/media/catalog/product/cache* sul server.

## Lettura correlata

[Controlla i cluster dedicati](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#check-dedicated-clusters) nella knowledge base di supporto.
