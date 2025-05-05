---
title: Passaggio a OpenSearch per Adobe Commerce su Cloud 2.4.4
promoted: true
description: Adobe Commerce su infrastruttura cloud 2.4.4 non supporterà le versioni di Elasticsearch successive alla versione 7.10. **Devi prima effettuare l’aggiornamento a Adobe Commerce 2.4.4 e quindi passare immediatamente da Elasticsearch a OpenSearch 1.2.x.**. L’Adobe fornirà istruzioni dettagliate più vicine alla versione GA di Adobe Commerce 2.4.4.
exl-id: 0cb34cee-d4d9-428e-a7fd-7301a86dd8f6
feature: Cloud, Iaas, Paas, Search, Services
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# Passaggio a OpenSearch per Adobe Commerce su Cloud 2.4.4

Adobe Commerce su infrastruttura cloud 2.4.4 non supporterà le versioni di Elasticsearch successive alla versione 7.10. **Devi prima eseguire l&#39;aggiornamento ad Adobe Commerce 2.4.4 e quindi passare immediatamente da Elasticsearch a OpenSearch 1.2.x.** L&#39;Adobe fornirà istruzioni dettagliate più vicine alla versione GA di Adobe Commerce 2.4.4.

>[!NOTE]
>
>Lo switch deve essere eseguito indipendentemente dal provider cloud.

Adobe Commerce on-premise aggiunge il supporto per l’Elasticsearch 7.16 e OpenSearch 1.2 in tutte le versioni di patch di marzo 2022 (2.4.4, 2.4.3-p2 e 2.3.7-p3). Nella versione 2.4.4, Adobe Commerce on cloud infrastructure passerà a OpenSearch come motore di ricerca predefinito, pertanto i commercianti devono utilizzare OpenSearch al posto di Elasticsearch prima di eseguire l’aggiornamento ad Adobe Commerce 2.4.4 o versione successiva. I commercianti con implementazioni on-premise di Adobe Commerce possono utilizzare Elasticsearch o OpenSearch perché Adobe Commerce continuerà a supportare entrambi.


## Cos’è OpenSearch?

OpenSearch è un fork di Elasticsearch e Kibana. È gestito da AWS al posto di Elastic.co. Per ulteriori informazioni, consulta GitHub [opensearch-project/OpenSearch](https://github.com/opensearch-project/OpenSearch).

**Compatibilità tra le versioni:**

**Adobe Commerce sull&#39;infrastruttura cloud supporterà l&#39;Elasticsearch 7.10?**

**Sì** - a partire da metà gennaio 2022, le versioni 2.4.3-p1, 2.4.3-p2 e 2.3.7-p3 di Adobe Commerce su infrastruttura cloud supportano l&#39;Elasticsearch 7.10.

Per Adobe Commerce on-premise, si consiglia la versione 7.16.x più recente per mitigare Log4j.

## Migrazione:

## Quando i commercianti possono migrare a OpenSearch?

Dopo Adobe Commerce 2.4.4.

Prima di iniziare il processo di aggiornamento ad Adobe Commerce 2.4.4, tuttavia, i commercianti devono utilizzare una versione corrente di Adobe Commerce che supporti l’Elasticsearch 7.10 ed essere in Elasticsearch almeno prima di iniziare il processo di aggiornamento a Adobe Commerce 2.4.4 o a OpenSearch.

## Cosa possono fare i commercianti (Adobe Commerce su infrastruttura cloud e Adobe Commerce on-premise) che non sono in versione 2.4.4? Possono effettuare l’aggiornamento a una versione supportata di Elasticsearch (7.10, 7.16.1) o a OpenSearch? Per farlo devono utilizzare l’ultima versione supportata (come 2.4.3-p1, 2.3.7-p2, 2.4.3-p1)?

Se la versione di base di Adobe Commerce su supporta l’Elasticsearch 7.10, può essere utilizzata.

Consulta [Requisiti di sistema](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html?lang=it) nella documentazione per gli sviluppatori per informazioni sulla compatibilità delle versioni.

>[!NOTE]
>
>Si consiglia di pianificare l’aggiornamento a Adobe Commerce 2.4.4 il prima possibile, in quanto l’Elasticsearch 7.10 sarà fine del ciclo di vita a maggio 2022.

I partner Adobe possono iscriversi al nostro programma beta [qui](https://experienceleague.adobe.com/docs/commerce-operations/release/beta-program.html?lang=it) per accedere al nostro ultimo codice beta4 testato in base all&#39;Elasticsearch 7.16.1 e OpenSearch 1.1.
