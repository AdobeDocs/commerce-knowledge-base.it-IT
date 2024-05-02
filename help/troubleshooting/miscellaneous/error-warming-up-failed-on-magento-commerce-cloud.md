---
title: "ERRORE: riscaldamento non riuscito in Adobe Commerce sull’infrastruttura cloud"
description: "Questo articolo fornisce una soluzione per quando la cache delle pagine si sta scaldando e non riesce con un errore:"
exl-id: 20a88030-b1c9-4fdc-83c1-f344d44cd2e1
feature: Cache, Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---

# ERRORE: riscaldamento non riuscito in Adobe Commerce sull’infrastruttura cloud

Questo articolo fornisce una soluzione per quando la cache delle pagine si sta scaldando e non riesce con un errore:

*ERRORE: riscaldamento non riuscito:`<website link>`*

## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud, tutto [versioni supportate](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

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

Assicurati di non aver abilitato il controllo degli accessi: passa al ramo/ambiente specifico e fai clic sul pulsante **Impostazioni** e controlla il **Controllo accesso HTTP** impostazione - in questo scenario non è possibile eseguire il riscaldamento della cache ed è necessario disabilitare il controllo degli accessi.

## Lettura correlata

* [Guida utente di Adobe Commerce > Cache a pagina intera](https://docs.magento.com/user-guide/system/cache-full-page.html) nella guida utente.
* [Riscaldamento della cache e sito non disponibile in Adobe Commerce](/help/troubleshooting/miscellaneous/cache-warming-up-and-site-unavailable-on-magento.md) nella nostra knowledge base di supporto.
