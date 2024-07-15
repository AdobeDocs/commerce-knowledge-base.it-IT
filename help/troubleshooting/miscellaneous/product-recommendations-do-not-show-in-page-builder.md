---
title: Recommendations del prodotto non visualizzato in Page Builder
description: Questo articolo fornisce una soluzione al problema in cui l’opzione Recommendations del prodotto non viene visualizzata in Page Builder.
exl-id: e96a446b-2e64-47a6-ac1b-e73183da9fb8
feature: Page Builder, Configuration, Personalization, Products, Recommendations
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# Recommendations del prodotto non visualizzato in Page Builder

Questo articolo fornisce una soluzione al problema in cui l’opzione Recommendations del prodotto non viene visualizzata in Page Builder.

## Prodotti e versioni interessati

* Adobe Commerce (tutti i metodi di distribuzione)

## Problema

L’opzione Recommendations del prodotto non viene visualizzata in Page Builder.

## Causa

In Page Builder non è disponibile alcuna opzione per aggiungere Product Recommendations. Il Recommendations di prodotto per Page Builder è un modulo opzionale e viene installato separatamente.

## Soluzione

1. Verificare di aver installato il modulo separatamente eseguendo il comando: `composer show magento/module-page-builder-product-recommendations`
1. Se restituisce il seguente messaggio: *Impossibile trovare il pacchetto magento/module-page-builder-recommendations*, installarlo eseguendo il comando: `composer require magento/module-page-builder-product-recommendations`

Attivando Product Recommendations in Page Builder, potrai [aggiungere un&#39;unità di consigli](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) a qualsiasi contenuto creato in Page Builder.

## Lettura correlata

* [Aggiungi contenuto - Recommendations del prodotto](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) nella guida utente.
* [Installa e configura il prodotto Recommendations](https://devdocs.magento.com/recommendations/install-configure.html) nella documentazione per gli sviluppatori.
* [Guida utente di Adobe Commerce](https://docs.magento.com/user-guide/)
