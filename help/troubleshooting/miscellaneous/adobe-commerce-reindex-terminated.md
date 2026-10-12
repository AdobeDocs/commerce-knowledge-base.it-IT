---
title: 'Adobe Commerce cloud: la reindicizzazione termina con il messaggio "Killed"'
description: '* Adobe Commerce su infrastruttura cloud (tutte le versioni)'
exl-id: 36ed9c9f-8280-41db-9df3-fe842dade4b1
feature: Cloud, Paas
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%
---
# Adobe Commerce cloud: reindicizzazione terminata con il messaggio `Killed`

## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud (tutte le versioni)

## Problema

Si sta tentando di eseguire una reindicizzazione nel ramo di integrazione (o nella gestione temporanea del progetto di architettura Starter) e il processo viene terminato con il messaggio `Killed`.

## Causa

Questo accade di solito perché i processi PHP stanno esaurendo la memoria.
Il motivo più comune è l’esistenza di un numero elevato di prodotti, store e/o gruppi di clienti nell’istanza.

## Soluzione

1. Riduci il numero di prodotti (nonché i gruppi di clienti e i negozi, se applicabile).
1. Limita l’utilizzo a uno o due utenti simultanei.
1. Disabilita i processi cron ed esegui manualmente in base alle esigenze.
1. Se non è già stato fatto in precedenza, richiedi un aggiornamento agli ambienti di integrazione avanzata . Tieni presente la restrizione sul numero di ambienti a cui verrai limitato una volta eseguito l’aggiornamento. Per ulteriori informazioni, consulta l&#39;articolo [Richiesta di miglioramento dell&#39;ambiente di integrazione - Pro e Starter](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27242) nella knowledge base di supporto.

## Lettura correlata:

Nella documentazione per gli sviluppatori:

* [Architettura Pro > Ambiente di integrazione](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment)
* [Architettura iniziale > Ambiente di staging](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#cloud-arch-stage)
