---
title: Adobe Commerce [!DNL crons] disabilitato senza intervento
description: Utilizzare questo articolo per risolvere il problema in cui [!DNL crons] sono disabilitati senza intervento.
exl-id: 5172d2ae-53ad-4db6-ae00-7b27c96911e9
source-git-commit: 9cd7cabc37c0f290c41f790b0fb06177c3156d48
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---

# Client Adobe Commerce disabilitati senza intervento

Questo articolo fornisce una soluzione per quando [!DNL crons] sono disabilitati senza intervento.

## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud, tutto [versioni supportate](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## Problema

Il tuo [!DNL crons] sono disattivati dopo la distribuzione.

<u>Passaggi da riprodurre</u>:

Distribuire.

<u>Risultato previsto</u>:

Il tuo [!DNL crons] è in esecuzione.

<u>Risultato effettivo</u>:

Il tuo [!DNL crons] sono disattivati dopo la distribuzione.

## Causa

Un problema relativo al [!DNL OPcache] impostazioni.

## Soluzione

Aggiorna [!DNL ECE Tools] alla versione più recente [2002.1.13.](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html#v2002113).

## Lettura correlata

* [Prestazioni lente, esecuzione lenta e prolungata [!DNL crons]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.html) nella nostra knowledge base di supporto.
* [[!DNL Cron] attività blocca le attività da altri gruppi](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-tasks-lock-tasks-from-other-groups.html?lang=en) nella nostra knowledge base di supporto.
* [[!DNL Cron] il processo è bloccato nello stato &quot;in esecuzione&quot;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=en) nella nostra knowledge base di supporto.
