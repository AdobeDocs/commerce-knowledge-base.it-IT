---
title: Adobe Commerce [!DNL crons] disabilitato senza intervento
description: Utilizza questo articolo per risolvere il problema in cui  [!DNL crons]  viene disabilitato senza intervento.
exl-id: 5172d2ae-53ad-4db6-ae00-7b27c96911e9
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---

# Client Adobe Commerce disabilitati senza intervento

Questo articolo fornisce una soluzione per i casi in cui [!DNL crons] viene disabilitato senza intervento.

## Prodotti e versioni interessati

* Adobe Commerce sull&#39;infrastruttura cloud, tutte le [versioni supportate](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## Problema

[!DNL crons] disabilitati dopo la distribuzione.

<u>Passaggi da riprodurre</u>:

Distribuire.

<u>Risultato previsto</u>:

[!DNL crons] è in esecuzione.

<u>Risultato effettivo</u>:

[!DNL crons] disabilitati dopo la distribuzione.

## Causa

Problema con le impostazioni [!DNL OPcache].

## Soluzione

Aggiorna [!DNL ECE Tools] alla versione più recente [2002.1.13](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package#v2002113).

## Lettura correlata

* [Prestazioni lente, esecuzione lenta e prolungata [!DNL crons]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.html?lang=it) nella Knowledge Base di supporto.
* [[!DNL Cron] le attività bloccano le attività da altri gruppi](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-tasks-lock-tasks-from-other-groups.html?lang=it) nella knowledge base di supporto.
* Il processo [[!DNL Cron] è bloccato nello stato &quot;in esecuzione&quot;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=it) nella knowledge base di supporto.
