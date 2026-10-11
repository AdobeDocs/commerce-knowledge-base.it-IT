---
title: La classificazione del dashboard e dei risultati di ricerca [!DNL Live Search] non è corretta
description: Questo articolo fornisce informazioni sulla risoluzione dei problemi se i dati nel dashboard [!DNL Live Search] non sono corretti o se la classificazione dei risultati della ricerca non è quella prevista.
feature: Admin Workspace, Categories, Search
role: Developer
exl-id: d4aea1f1-c2c4-45e5-87c8-73069f7c9ffd
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%
---
# La classificazione del dashboard e dei risultati di ricerca [!DNL Live Search] non è corretta

Se si nota che i dati visualizzati nel dashboard [!DNL Live Search] non sono corretti o se la [classificazione dei risultati della ricerca](https://experienceleague.adobe.com/it/docs/commerce-merchant-services/live-search/live-search-admin/category-merch#ranking-strategies) non è quella prevista, vedere quanto segue per possibili motivi:

* Manca il campo `topLevelSku` del contesto di prodotto negli eventi `productView`. Questo causa conversioni vuote e altre metriche impreviste.

* Il campo `productContext` dell&#39;evento `add-to-cart` non è impostato e popolato.

* Il tipo di ambiente non è corretto. Ad esempio, se l&#39;ambiente è impostato su *[!UICONTROL Testing]* invece di *[!UICONTROL Production]*. Per ulteriori informazioni, vedere [Contesto Storefront](https://github.com/adobe/commerce-events/blob/main/examples/events/example-contexts/mock-storefront-context.md).

* Contesto dei risultati di ricerca mancante nell&#39;evento [search-product-click](https://github.com/adobe/commerce-events/blob/main/examples/events/search-product-click.md).
