---
title: Il `Magento-cloud` [!DNL CLI] non mostra un ambiente attivo
description: Questo articolo descrive un problema noto di Adobe Commerce per cui "Magento-cloud" [!DNL CLI] (strumento da riga di comando) non mostra un ambiente attivo.
feature: Cloud, Integration, Configuration
role: Developer
exl-id: 3c1b5de2-8888-4531-9dc1-cd478e3c96fc
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: cc04bd17-78d5-5120-8c3d-1b8a57e49280
    internal-label: Integration
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '136'
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
