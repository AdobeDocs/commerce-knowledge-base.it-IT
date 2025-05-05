---
title: Il &grave;Magento-cloud&grave; [!DNL CLI] non mostra un ambiente attivo
description: Questo articolo descrive un problema noto di Adobe Commerce in cui "Magento-cloud" [!DNL CLI] (strumento da riga di comando) non mostra un ambiente attivo.
feature: Cloud, Integration, Configuration
role: Developer
exl-id: 3c1b5de2-8888-4531-9dc1-cd478e3c96fc
source-git-commit: 5eac8bb54e205eff6a96e279295cd12db1009f0a
workflow-type: tm+mt
source-wordcount: '124'
ht-degree: 0%

---

# `Magento-cloud` [!DNL CLI] non mostra un ambiente attivo

## Problema

Sono presenti diversi ambienti attivi e si sta tentando di interagire con un ambiente eseguendo un comando `Magento-cloud` [!DNL CLI] (strumento da riga di comando). (Ad esempio: `ssh`, `db:size`, `db:sql`, ecc.)
Tuttavia, la richiesta di scegliere l’ambiente desiderato non elenca questo ambiente. (ad esempio: ambiente di integrazione)

```
Enter a number to choose an environment:
Default: master
  [0] integration2 (type: development)
  [1] master (type: development)
  [2] production
  [3] staging
 >
```

## Causa

L’ambiente potrebbe non essere disponibile a causa di una distribuzione in corso, bloccata o non riuscita.

## Soluzione

Sarà necessario specificare manualmente l&#39;ambiente con il flag `e|-environment`.

1. Trova l’elenco degli ambienti attivi e prendi nota dei nomi degli ambienti:

```
$ magento-cloud environment: list |grep "Active\|ID"
Your environments are:

| ID                     | Title            | Status       | Type           |
| Master                 | Master           | Active       | Development    |
|   Production           | Production       | Active       | Production     |
|     Staging            | Staging          | Active       | Staging        |
|       Integration      | Integration      | Active       | Development    |
|          Integration 2 | Integration 2    | Active       | Development    |
```

2.Specificare l&#39;ID dell&#39;ambiente con il comando:

`magento-cloud ssh -e integration`
