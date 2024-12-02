---
title: Modifica del prezzo di base influisce sul prezzo di catalogo condiviso
description: 'Questo articolo risponde alla domanda: se un prodotto in un catalogo condiviso ha un prezzo personalizzato e il prezzo di base del prodotto cambia (ad esempio dopo un aggiornamento pianificato), quale prezzo si applica nel catalogo condiviso?'
exl-id: 916678c1-ada6-4f23-af16-b107cb83ff16
feature: Catalog Management
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%

---

# Modifica del prezzo di base influisce sul prezzo di catalogo condiviso

Questo articolo risponde alla domanda: se un prodotto in un catalogo condiviso ha un prezzo personalizzato e il prezzo di base del prodotto cambia (ad esempio dopo un aggiornamento pianificato), quale prezzo si applica nel catalogo condiviso?

## Con il prezzo personalizzato impostato su Percentuale, cambia anche il prezzo del catalogo condiviso

Se il prezzo personalizzato di un prodotto in un catalogo condiviso è stato impostato su Percentuale, il prezzo del catalogo condiviso del prodotto viene aggiornato in modo implicito dopo la modifica del prezzo di base.

In altre parole, quando il prezzo di base viene aggiornato (tramite un aggiornamento normale o pianificato), anche il prezzo di catalogo condiviso cambia dopo l’applicazione dello sconto percentuale.

## Con il prezzo personalizzato impostato su Fisso, il prezzo del catalogo condiviso non cambia

Se il prezzo personalizzato per un prodotto in un catalogo condiviso è stato impostato su Fisso, il prezzo nel catalogo condiviso non cambia mai, indipendentemente dal modo in cui viene aggiornato il prezzo di base (tramite aggiornamento pianificato, Amministrazione di Adobe Commerce, API o importazione).

## Storefront visualizza sempre il prezzo più basso disponibile

Se il prezzo base del prodotto cambia e diventa inferiore al prezzo di catalogo condiviso corrispondente, Storefront visualizza il prezzo base come prezzo più basso disponibile nel sistema.

## Lettura correlata

[Impostare i prezzi e la struttura per un catalogo condiviso](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/define/catalog-shared-pricing-structure.html) nella guida utente.
