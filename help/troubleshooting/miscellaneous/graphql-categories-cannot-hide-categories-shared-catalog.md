---
title: Query GraphQL per nascondere le categorie che non funzionano con il catalogo condiviso B2B
description: Questo articolo fornisce una soluzione per i casi in cui la funzione di catalogo condiviso B2B non funzioni con la query delle categorie di GraphQL per nascondere le categorie.
exl-id: bdafa8d9-b637-409e-86b5-d132bccfe0b8
feature: B2B, Catalog Management, Categories, GraphQL, Customer Service
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# Query GraphQL per nascondere le categorie che non funzionano con il catalogo condiviso B2B


## Prodotti e versioni interessati

* Adobe Commerce sull’infrastruttura cloud e Adobe Commerce on-premise 2.4.3

## Problema

Le categorie di GraphQL e le query `categoryList` ignorano l&#39;autorizzazione della categoria per nascondere le categorie in un catalogo condiviso. Questo accade a tutti i commercianti su Adobe Commerce 2.4.3 con la funzione Catalogo condiviso B2B attivata.

<u>Passaggi da riprodurre</u>:

Prerequisiti:

Questo accade a tutti i commercianti su Adobe Commerce 2.4.3 con vetrina PWA che utilizzano API GraphQL con backend/amministratore Adobe Commerce che dispone della funzione Catalogo condiviso B2B attivata.

1. Creare più categorie (CAT1,CAT2).
1. Crea un catalogo condiviso privato.
1. Crea un utente aziendale e assegnalo al catalogo condiviso di cui sopra.
1. Assegna alcuni prodotti a ciascuna di queste categorie.
1. Assegna CAT1 al catalogo personalizzato, rimuovi l’assegnazione di CAT2 dal catalogo privato personalizzato. Questo annulla l’assegnazione di tutti i prodotti da CAT2 dal catalogo condiviso.
1. Salva il catalogo personalizzato.
1. Impostare l&#39;autorizzazione per la categoria per CAT2 su *Nega* categoria esplorazione e impostare il gruppo di clienti sul catalogo privato sopra riportato.
1. Eseguire la query `categoryList query` o le categorie come utente della società dal passaggio tre.

<u>Risultati previsti</u>:

Solo il CAT1 viene visualizzato nei risultati.

<u>Risultati effettivi</u>:

Tutte le categorie vengono visualizzate indipendentemente dal fatto che siano assegnate o meno al catalogo condiviso o dalle relative autorizzazioni.

## Causa

Funzionalità non implementata.

## Soluzione

Il problema verrà risolto nell&#39;ambito della versione 2.4.4 e gli esercenti devono [inviare un ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) per ottenere una patch personalizzata se necessitano di una soluzione prima della versione 2.4.4.

## Lettura correlata

* [Limiti per il numero di categorie secondo le best practice di Adobe Commerce](https://support.magento.com/hc/en-us/articles/360048176832) nella Knowledge Base di supporto.
