---
title: Ripristino manuale dei processi bloccati di Adobe Commerce sull’infrastruttura cloud cron
description: i processi cron di Adobe Commerce su infrastruttura cloud non vengono completati, rimangono bloccati e impediscono l’esecuzione di altri processi cron. Questo articolo mostra come ripristinare manualmente i processi bloccati del cron.
exl-id: aec6de8e-c3a9-4a6d-8ecd-a213e77c97a1
feature: Cloud
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '165'
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

[Ripristina processi cron](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=it)
