---
title: Ripristino manuale dei processi bloccati di Adobe Commerce sull’infrastruttura cloud cron
description: i processi cron di Adobe Commerce su infrastruttura cloud non vengono completati, rimangono bloccati e impediscono l’esecuzione di altri processi cron. Questo articolo mostra come ripristinare manualmente i processi bloccati del cron.
exl-id: aec6de8e-c3a9-4a6d-8ecd-a213e77c97a1
feature: Cloud
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%
---
# Ripristino manuale dei processi bloccati di Adobe Commerce sull’infrastruttura cloud cron

i processi cron di Adobe Commerce su infrastruttura cloud non vengono completati, rimangono bloccati e impediscono l’esecuzione di altri processi cron. Questo articolo mostra come ripristinare manualmente i processi bloccati del cron.

Utilizzare questo comando con cautela. Per ulteriori dettagli, si consiglia di leggere l&#39;articolo [Ripristina processi cron](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=it) nella Knowledge Base di supporto.

## Passaggi

>[!INFO]
>
>Da [ECE-Tools v2002.0.4](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-release-archive.html?lang=it#v2002.0.4) è possibile reimpostare manualmente i processi cron bloccati utilizzando un comando CLI tramite accesso SSH.

1. [SSH nell&#39;ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=it).
1. Esegui questo comando: `./vendor/bin/ece-tools cron:unlock`

## Avvisi

* Il comando ripristina **tutti** processi cron, inclusi quelli attualmente in esecuzione; **utilizzarlo solo in casi eccezionali**.
* Evita di utilizzare questa soluzione quando gli indicizzatori sono in esecuzione.

## Leggilo nella nostra knowledge base di supporto:

[Reimposta processi cron](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=it)
