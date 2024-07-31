---
title: La classificazione del dashboard e dei risultati di ricerca '[!DNL Live Search]' non è corretta
description: In questo articolo vengono fornite informazioni sulla risoluzione dei problemi se i dati nel dashboard  [!DNL Live Search]  non sono corretti o se la classificazione dei risultati della ricerca non è quella prevista.
feature: Admin Workspace, Categories, Search
role: Developer
source-git-commit: 4c1199c31f83d7c2aaf28e259d63473779bf2efe
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 0%

---

# La classificazione del dashboard e dei risultati di ricerca [!DNL Live Search] non è corretta

Se si nota che i dati visualizzati nel dashboard [!DNL Live Search] non sono corretti o se la [classificazione dei risultati della ricerca](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-admin/category-merch#ranking-strategies) non è quella prevista, vedere quanto segue per possibili motivi:

* Manca il campo `topLevelSku` del contesto di prodotto negli eventi `productView`. Questo causa conversioni vuote e altre metriche impreviste.

* Il campo `productContext` dell&#39;evento `add-to-cart` non è impostato e popolato.

* Il tipo di ambiente non è corretto. Ad esempio, se l&#39;ambiente è impostato su *[!UICONTROL Testing]* invece di *[!UICONTROL Production]*. Per ulteriori informazioni, vedere [Contesto Storefront](https://github.com/adobe/commerce-events/blob/main/examples/events/example-contexts/mock-storefront-context.md).

* Contesto dei risultati di ricerca mancante nell&#39;evento [search-product-click](https://github.com/adobe/commerce-events/blob/main/examples/events/search-product-click.md).
