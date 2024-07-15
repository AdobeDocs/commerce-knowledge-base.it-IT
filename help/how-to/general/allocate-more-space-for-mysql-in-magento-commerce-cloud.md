---
title: Alloca più spazio per MySQL in Adobe Commerce sul cloud
description: Questo articolo fornisce istruzioni su come allocare più spazio per MySQL in Adobe Commerce sull’infrastruttura cloud.
exl-id: 98501aa0-5ec7-4ea1-8856-13d171ad0be9
feature: Cloud
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# Alloca più spazio per MySQL in Adobe Commerce sul cloud


## Allocazione di spazio per l&#39;integrazione di piani Starter e Pro

Per tutti gli ambienti del piano Starter e Pro [Integration environment](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md), è possibile allocare più spazio per MySQL nel file `.magento/services.yaml` aumentando il parametro `mysql: disk:`. Ad esempio:

```yaml
mysql:
    type: mysql:10.0
    disk: 2048
```

Per ulteriori informazioni, vedere l&#39;articolo [Configurazione del servizio MySQL](https://devdocs.magento.com/guides/v2.3/cloud/project/project-conf-files_services-mysql.html).

Dopo aver modificato il file `.magento/services.yaml`, è necessario eseguire il commit e inviare le modifiche in push per applicarle. Il push attiverà il processo di distribuzione.

>[!WARNING]
>
>Una partizione del piano Starter non dovrebbe mai essere ridotta (ad esempio, passando da 30 GB a 20 GB), in quanto ciò potrebbe causare un danneggiamento catastrofico dei dati.

## Allocazione di spazio su produzione o staging piano Pro

Per apportare queste modifiche all&#39;ambiente di gestione temporanea o di produzione del piano Pro, è necessario creare un [ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#merchant-not-displayed). Quando si invia un ticket di supporto per aumentare lo spazio di archiviazione, il supporto dovrà sapere la quantità e la partizione a cui applicare lo spazio di archiviazione (`/mysql` o `/exports`). Una richiesta di aumento dello storage richiede l&#39;approvazione del team dell&#39;account Adobe, che esaminerà la quantità di storage autorizzata (come indicato nel modulo d&#39;ordine) prima dell&#39;approvazione.

## Riduzione dello spazio allocato non disponibile (piano Pro e Starter)

Il supporto Adobe Commerce consente di espandere una partizione (`/mysql` o `/exports`), ma non di ridurre una partizione. Questa operazione comporta il rischio di danneggiamento dei dati ed è per questo che non è disponibile una riduzione dello spazio di archiviazione per una partizione.
Lo stesso vale per il piano Starter, in cui è possibile aumentare autonomamente lo spazio allocato: la riduzione non è consigliata e potrebbe causare un danneggiamento catastrofico dei dati.
