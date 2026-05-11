---
title: Impossibile visualizzare più spazi di dati SaaS dopo la configurazione delle chiavi API di Adobe AI
description: Questo articolo fornisce una soluzione per i problemi in cui viene visualizzato un solo spazio dati SaaS dopo aver configurato le chiavi API per Adobe AI.
exl-id: e13041da-b122-4684-8287-42132931f47a
feature: REST, Saas, Observability
role: Developer
source-git-commit: 61f5a526a0c36c91739103c0802bc9794a425f38
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# Impossibile visualizzare più spazi di dati SaaS dopo la configurazione delle chiavi API di Adobe AI

Dopo aver configurato le chiavi API per un servizio Commerce, come i servizi Adobe AI (Product Recommendations o Live Search) o Payment Services per Adobe Commerce, prevedi di visualizzare più spazi dati SaaS nel connettore dei servizi Commerce. A seconda dell’adesione al prodotto e del tipo di distribuzione, il connettore visualizza un solo spazio di dati SaaS, il che rappresenta il comportamento previsto.

## Prodotti e versioni interessati

* Adobe Commerce (tutti i metodi di distribuzione): tutte le versioni
* Magento Open Source: tutte le versioni
* Estensione o tecnologia (Fastly, New Relic, ecc.), Adobe AI (Product Recommendations/Live Search)

## Problema

Dopo aver configurato le chiavi API di Adobe AI, il sistema mostra un solo spazio di dati SaaS.

## Causa

Il numero di spazi di dati SaaS disponibili dipende dalla licenza del prodotto associata all’account Commerce e dal tipo di servizio utilizzato.

## Soluzione

In generale, il numero di spazi di dati SaaS disponibili dipende dalla licenza Commerce:

* Adobe Commerce: uno spazio dati di produzione e due spazi dati di test
* Magento Open Source: uno spazio dati di produzione e nessuno spazio dati di test

Per i servizi di pagamento, il comportamento predefinito è:

* Per impostazione predefinita, Payment Services su Adobe Commerce (*Cloud o locale*) dispone di tre spazi dati:
* uno spazio di dati di produzione
* due spazi di dati di prova
* Payment Services su Magento Open Source dispone di uno spazio dati per impostazione predefinita

I clienti che possiedono più progetti Cloud o installazioni on-premise (*live/production*) possono anche richiedere spazi di dati aggiuntivi per la produzione e il testing per ciascun progetto o istanza inviando una richiesta di supporto.

I clienti Magento Open Source che utilizzano Adobe Payment Services possono richiedere anche uno spazio di dati aggiuntivo. Contatta il team dei pagamenti per l’approvazione preventiva prima di inviare una richiesta di supporto per aggiungere uno spazio dati di test.

>[!NOTE]
> * Non utilizzare lo stesso spazio di dati SaaS in più ambienti contemporaneamente. Se uno spazio dati di produzione o di test viene riutilizzato in più ambienti, i dati possono combinarsi e richiedere una pulizia.
> * Per impostazione predefinita, i servizi di pagamento in Adobe Commerce (*Cloud/On-Prem*) dispongono di tre spazi di dati.
> * Payment Services su Magento Open Source dispone di uno spazio dati per impostazione predefinita.
> Per richiedere spazi di dati aggiuntivi:
> * I clienti Magento Open Source che utilizzano Adobe Payment Services possono richiedere uno spazio di dati aggiuntivo. Contatta il team dei pagamenti per l’approvazione preventiva prima di inviare una richiesta di supporto per ottenere uno spazio dei dati per i test.
> * I clienti che possiedono più progetti Cloud o installazioni on-premise (*live/production*) possono anche richiedere spazi di dati aggiuntivi per la produzione e il testing per ciascun progetto o istanza inviando una richiesta di supporto.

## Lettura completata

[Provisioning dello spazio dati SaaS](https://experienceleague.adobe.com/it/docs/commerce/user-guides/integration-services/saas?lang=en#saas-data-space-provisioning)
