---
title: "E-mail che indica che l’archiviazione delle esportazioni è quasi piena"
description: Questo articolo fornisce una soluzione al problema in cui si riceve un messaggio e-mail che informa che lo spazio di archiviazione per le esportazioni è quasi pieno.
feature: Cloud, Storage, Media
role: Developer
source-git-commit: 8f783cb4245911bded5e9946917e2f2c3e78a705
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---

# E-mail che indica che l’archiviazione delle esportazioni è quasi piena

Questo articolo fornisce una soluzione al problema in cui si riceve un messaggio e-mail che informa che lo spazio di archiviazione per le esportazioni è quasi pieno.

## Prodotti e versioni interessati

Adobe Commerce su infrastruttura cloud (tutte le versioni)

## Problema

Ricevi un’e-mail con il seguente contenuto ma non riesci a individuare *esportazioni* cartella:

*Il monitoraggio ha rilevato che l&#39;archivio &quot;esportazioni&quot; nel cluster XXX è pieno all&#39;incirca all&#39;85%.*
*Se necessario, controlla l’utilizzo, effettua una pulizia o richiedi un upsize.*
*Inoltre, si noti che verrà eseguito automaticamente un upsize quando lo storage raggiunge il livello di soglia critica.*

## Causa

L’e-mail fa riferimento al **esportazioni** di archiviazione, ovvero la quantità di disco allocata ai file/supporti e non a una cartella specifica denominata *esportazioni*.

## Soluzione

È necessario verificare l’utilizzo dei file nell’ambiente. Esegui questo comando per ottenere l’utilizzo esistente:

`df -h |grep data`

Le posizioni tipiche in cui l&#39;archiviazione dei file è probabilmente riempita sono *pub/media/catalog/product/cache* o *var/log* cartelle. Per determinare lo spazio su disco utilizzato dai file, eseguire questo comando con il percorso appropriato */path/to/folder*:

`du -shc` */path/to/folder*

Se l&#39;utilizzo del disco rappresenta una percentuale elevata dello spazio totale su disco, è consigliabile attivare [Ottimizzazione Fastly Deep Image](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization#deep-image-optimization), quindi eliminare i file in *pub/media/catalog/product/cache* sul server manualmente.

## Lettura correlata

[Controlla cluster dedicati](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#check-dedicated-clusters) nella nostra knowledge base di supporto.