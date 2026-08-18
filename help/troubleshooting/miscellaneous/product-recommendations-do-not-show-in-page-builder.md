---
title: Consigli di prodotto non visualizzati in Page Builder
description: Questo articolo fornisce una soluzione per il problema in cui l’opzione Consigli di prodotto non viene visualizzata in Page Builder.
exl-id: e96a446b-2e64-47a6-ac1b-e73183da9fb8
feature: Page Builder, Configuration, Personalization, Products, Recommendations
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---

# Consigli di prodotto non visualizzati in Page Builder

Questo articolo fornisce una soluzione per il problema in cui l’opzione Consigli di prodotto non viene visualizzata in Page Builder.

## Prodotti e versioni interessati

* Adobe Commerce (tutti i metodi di distribuzione)

## Problema

L’opzione Consigli di prodotto non viene visualizzata in Page Builder.

## Causa

In Page Builder non è disponibile alcuna opzione per aggiungere Consigli di prodotto. Consigli di prodotto per Page Builder è un modulo opzionale e viene installato separatamente.

## Soluzione

1. Verificare di aver installato il modulo separatamente eseguendo il comando: `composer show magento/module-page-builder-product-recommendations`
1. Se restituisce il seguente messaggio: *Impossibile trovare il pacchetto magento/module-page-builder-recommendations*, installarlo eseguendo il comando: `composer require magento/module-page-builder-product-recommendations`

Attivando Consigli di prodotto in Page Builder, potrai [aggiungere un&#39;unità di consigli](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) a qualsiasi contenuto creato in Page Builder.

## Lettura correlata

* [Aggiungi contenuto - Consigli di prodotto](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) nella nostra guida utente.
* [Installa e configura Product Recommendations](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/getting-started/install-configure) nella documentazione per gli sviluppatori.
* [Guida utente di Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-admin/user-guides/home)
