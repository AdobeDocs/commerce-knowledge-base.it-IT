---
title: Installare le ultime patch per risolvere i problemi di Adobe Commerce Redis
description: Questo articolo fornisce informazioni sulle ultime patch relative a Redis disponibili nel pacchetto [Adobe Commerce sulle patch dell’infrastruttura cloud](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).
exl-id: 0335bc11-f679-4629-b4e7-6a0e68c3ae44
feature: Cache, Install, Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---

# Installare le ultime patch per risolvere i problemi di Adobe Commerce Redis

Questo articolo fornisce informazioni sulle ultime patch relative a Redis disponibili nel pacchetto [Adobe Commerce sulle patch dell&#39;infrastruttura cloud](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## Prodotti e versioni interessati

Adobe Commerce sull’infrastruttura cloud 2.3.3, 2.3.4

## Problema

L&#39;utilizzo aggiuntivo di CPU e memoria da parte di Redis potrebbe ridurre le prestazioni di Adobe Commerce e quindi le prestazioni complessive del sito Web.

## Soluzione

Applica le ultime patch fornite da Adobe Commerce sul pacchetto di patch per l’infrastruttura cloud. Per istruzioni dettagliate, consulta [Applicare le patch](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

Le ultime patch Redis distribuite dal pacchetto Adobe Commerce sulle patch dell’infrastruttura cloud contribuiscono a:

* riduzione delle dimensioni delle comunicazioni di rete per Redis
* risoluzione di problemi di tipo &quot;race condition&quot; che determinano un maggiore consumo di memoria
* modifica della scheda cache per coprire i casi di rimozione
* riduzione del consumo di CPU Redis

Adobe Commerce consiglia inoltre di eseguire l’aggiornamento a Redis 5, se utilizzi Adobe Commerce sull’infrastruttura cloud 2.3.3 o versione successiva.
