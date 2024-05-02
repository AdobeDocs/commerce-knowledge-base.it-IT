---
title: '"Adobe Commerce cloud: la reindicizzazione termina con il messaggio "Killed"'
description: '* Adobe Commerce su infrastruttura cloud (tutte le versioni)'
exl-id: 36ed9c9f-8280-41db-9df3-fe842dade4b1
feature: Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# Adobe Commerce cloud: reindicizzazione terminata con `Killed` messaggio

## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud (tutte le versioni)

## Problema

Stai tentando di eseguire una reindicizzazione nel ramo di integrazione (o nella gestione temporanea del progetto di architettura Starter) e il processo viene terminato con `Killed` messaggio.

## Causa

Questo accade di solito perché i processi PHP stanno esaurendo la memoria.
Il motivo più comune è l’esistenza di un numero elevato di prodotti, store e/o gruppi di clienti nell’istanza.

## Soluzione

1. Riduci il numero di prodotti (nonché i gruppi di clienti e i negozi, se applicabile).
1. Limita l’utilizzo a uno o due utenti simultanei.
1. Disabilita i processi cron ed esegui manualmente in base alle esigenze.
1. Se non è già stato fatto in precedenza, richiedi un aggiornamento agli ambienti di integrazione avanzata . Tieni presente la restrizione sul numero di ambienti a cui verrai limitato una volta eseguito l’aggiornamento. Consulta la sezione [Richiesta di miglioramento dell’ambiente di integrazione - Pro e Starter](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) articolo nella knowledge base di supporto per i dettagli.

## Lettura correlata:

Nella documentazione per gli sviluppatori:

* [Architettura Pro > Ambiente di integrazione](https://devdocs.magento.com/cloud/architecture/pro-architecture.html#cloud-arch-int)
* [Architettura iniziale > Ambiente di staging](https://devdocs.magento.com/cloud/architecture/starter-architecture.html#cloud-arch-stage)
