---
title: La classificazione del dashboard e dei risultati di ricerca [!DNL Live Search] non è corretta
description: In questo articolo vengono fornite informazioni sulla risoluzione dei problemi se i dati nel dashboard  [!DNL Live Search]  non sono corretti o se la classificazione dei risultati della ricerca non è quella prevista.
feature: Admin Workspace, Categories, Search
role: Developer
exl-id: d4aea1f1-c2c4-45e5-87c8-73069f7c9ffd
source-git-commit: 9bb839292a120a3dab5151d493f915619dbf5c06
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 0%

---

# La classificazione del dashboard e dei risultati di ricerca [!DNL Live Search] non è corretta

Se si nota che i dati visualizzati nel dashboard [!DNL Live Search] non sono corretti o se la [classificazione dei risultati della ricerca](https://experienceleague.adobe.com/it/docs/commerce-merchant-services/live-search/live-search-admin/category-merch#ranking-strategies) non è quella prevista, vedere quanto segue per possibili motivi:

* Manca il campo `topLevelSku` del contesto di prodotto negli eventi `productView`. Questo causa conversioni vuote e altre metriche impreviste.

* Il campo `productContext` dell&#39;evento `add-to-cart` non è impostato e popolato.

* Il tipo di ambiente non è corretto. Ad esempio, se l&#39;ambiente è impostato su *[!UICONTROL Testing]* invece di *[!UICONTROL Production]*. Per ulteriori informazioni, vedere [Contesto Storefront](https://github.com/adobe/commerce-events/blob/main/examples/events/example-contexts/mock-storefront-context.md).

* Contesto dei risultati di ricerca mancante nell&#39;evento [search-product-click](https://github.com/adobe/commerce-events/blob/main/examples/events/search-product-click.md).
