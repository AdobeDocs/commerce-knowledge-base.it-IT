---
title: "ERRORE: riscaldamento non riuscito in Adobe Commerce sull’infrastruttura cloud"
description: "Questo articolo fornisce una soluzione per quando la cache delle pagine si sta scaldando e non riesce con un errore:"
exl-id: 20a88030-b1c9-4fdc-83c1-f344d44cd2e1
feature: Cache, Cloud, Paas
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---

# ERRORE: riscaldamento non riuscito in Adobe Commerce sull’infrastruttura cloud

Questo articolo fornisce una soluzione per quando la cache delle pagine si sta scaldando e non riesce con un errore:

*ERRORE: riscaldamento non riuscito:`<website link>`*

## Prodotti e versioni interessati

* Adobe Commerce sull&#39;infrastruttura cloud, tutte le [versioni supportate](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problema

Riscaldamento della cache non riuscito.

<u>Passaggi da riprodurre</u>:

Avviare le operazioni di riscaldamento della cache.

<u>Risultato previsto</u>:

Caricamenti di pagine o dell’intero sito.

<u>Risultato effettivo</u>:

Il sito non è disponibile o il tempo di risposta è troppo alto. *ERRORE: riscaldamento non riuscito:`<website link>`*

## Causa

Il riscaldamento della cache non funziona se è abilitato il controllo degli accessi HTTP.

## Soluzione

Verificare che il controllo degli accessi non sia abilitato: accedere al ramo/ambiente specifico, fare clic sull&#39;icona **Impostazioni** e controllare l&#39;impostazione **Controllo degli accessi HTTP**. In questo caso non è possibile eseguire il riscaldamento della cache e il controllo degli accessi deve essere disabilitato.

## Lettura correlata

* [Guida utente di Adobe Commerce > Cache a pagina intera](https://experienceleague.adobe.com/it/docs/commerce-admin/systems/tools/cache-management#full-page-caching) nella guida utente.
* [Riscaldamento della cache e sito non disponibile in Adobe Commerce](/help/troubleshooting/miscellaneous/cache-warming-up-and-site-unavailable-on-magento.md) nella Knowledge Base di supporto.
