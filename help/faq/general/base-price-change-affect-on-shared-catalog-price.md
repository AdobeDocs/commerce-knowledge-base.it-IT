---
title: Modifica del prezzo di base influisce sul prezzo di catalogo condiviso
description: 'Questo articolo risponde alla domanda: se un prodotto in un catalogo condiviso ha un prezzo personalizzato e il prezzo di base del prodotto cambia (ad esempio dopo un aggiornamento pianificato), quale prezzo si applica nel catalogo condiviso?'
exl-id: 916678c1-ada6-4f23-af16-b107cb83ff16
feature: Catalog Management
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '274'
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
