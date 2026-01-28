---
title: Ho configurato le chiavi API per l’intelligenza artificiale di Adobe ma visualizzo un solo spazio dati SaaS
description: Questo articolo fornisce una soluzione per i problemi in cui visualizzi un solo spazio dati SaaS dopo aver configurato le chiavi API per l’intelligenza artificiale di Adobe.
exl-id: e13041da-b122-4684-8287-42132931f47a
feature: REST, Saas, Observability
role: Developer
source-git-commit: 27b0836380c3040b26076b9cb81b9328cb2c9ff2
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# Ho configurato le chiavi API per l’intelligenza artificiale di Adobe ma visualizzo un solo spazio dati SaaS

Questo articolo fornisce una soluzione per i problemi in cui visualizzi un solo spazio dati SaaS dopo aver configurato le chiavi API per l’intelligenza artificiale di Adobe.

## Prodotti e versioni interessati

* Adobe Commerce (tutti i metodi di distribuzione): tutte le versioni
* Magento Open Source: tutte le versioni
* Estensione o tecnologia (Fastly, New Relic, ecc.), IA per Adobe (Product Recommendations/Live Search)

## Problema

Ho configurato le chiavi API per l’intelligenza artificiale di Adobe, ma visualizzo un solo spazio dati SaaS.

## Causa

Il numero di spazi di dati SaaS visualizzati dipende dalla licenza Commerce:

* Adobe Commerce: uno spazio dati di produzione; due spazi dati di test
* Magento Open Source: uno spazio dati di produzione; nessuno spazio dati di test

## Soluzione

* Assicurati che le chiavi API siano state create nell’account del proprietario dell’account. Anche se ti è stato concesso l’accesso condiviso al loro account e hai creato le chiavi sul tuo account, questo non ti concederà più di uno spazio di dati.
* Se le chiavi sono state generate nell&#39;account del proprietario dell&#39;account, verificare che la licenza sia attiva, ovvero che non siano presenti fatture in sospeso.
