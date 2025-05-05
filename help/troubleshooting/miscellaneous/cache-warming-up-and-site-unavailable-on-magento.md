---
title: Riscaldamento della cache e sito non disponibile in Adobe Commerce
description: Questo articolo fornisce una soluzione per quando la cache delle pagine si sta riscaldando ed è presente una distribuzione bloccata o un sito inattivo.
exl-id: c91d5c1f-95e6-4240-be98-2acea49ae728
feature: Cache, Variables
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---

# Riscaldamento della cache e sito non disponibile in Adobe Commerce

Questo articolo fornisce una soluzione per quando la cache delle pagine si sta riscaldando ed è presente una distribuzione bloccata o un sito inattivo.

## Prodotti e versioni interessati

* Adobe Commerce sull&#39;infrastruttura cloud, tutte le [versioni supportate](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problema

Lo script di riscaldamento della cache, al termine della fase di post-distribuzione, invia le richieste a una frequenza talmente elevata che alcune istanze, come quelle a 4 CPU, non possono gestirle. Il loro indice esaurisce il numero di lavoratori.

<u>Passaggi da riprodurre</u>:

Avvia le operazioni di riscaldamento della cache.

<u>Risultato previsto</u>:

Caricamenti di pagine o dell’intero sito.

<u>Risultato effettivo</u>:

Il sito non è disponibile o il tempo di risposta è troppo alto.

## Soluzione

Limita il numero di connessioni simultanee durante il riscaldamento della cache. È necessario aggiungere la variabile post-distribuzione `WARM_UP_CONCURRENCY` per specificare il numero di richieste di riscaldamento che lo script di riscaldamento della cache può inviare contemporaneamente. Impostando questa opzione è possibile gestire il carico sull’infrastruttura cloud di Adobe Commerce. Per i passaggi, consulta [Variabili post-distribuzione > WARM\_UP\_CONCURRENCY](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-post-deploy#warm_up_concurrency) nella documentazione per gli sviluppatori.

## Lettura correlata

[Cache a pagina intera](https://experienceleague.adobe.com/it/docs/commerce-admin/systems/tools/cache-management#full-page-caching) nella guida utente
