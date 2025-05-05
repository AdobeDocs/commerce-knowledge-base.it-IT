---
title: Errore [!DNL opensearch] motore di ricerca inesistente. Ripristino di  [!DNL livesearch].
description: Questo articolo fornisce una soluzione al problema in cui viene visualizzato l'errore, "Error- [!DNL opensearch] search engine does not exist. Ripristino di  [!DNL livesearch].&grave; in Adobe Commerce su infrastruttura cloud.
feature: Deploy, Search
role: Developer
exl-id: a6cc981d-b8f0-402d-8771-60d2f21f09f8
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---

# Errore [!DNL opensearch] motore di ricerca inesistente. Ripristino di [!DNL livesearch].

Questo articolo fornisce una soluzione al problema in cui viene visualizzato l&#39;errore: *Errore: [!DNL opensearch] il motore di ricerca non esiste. Ripristino di [!DNL livesearch].* in Adobe Commerce sull&#39;infrastruttura cloud in cui viene utilizzato [!DNL Live Search].

## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud, tutte le versioni
* [!DNL Live Search] è installato e in uso

## Problema

Il seguente messaggio viene visualizzato nei registri (e osservabile in [!DNL New Relic]):
*Errore: il motore di ricerca [!DNL opensearch] non esiste. Ripristino di [!DNL livesearch].* in corso

## Soluzione

1. Modificare il file `.magento.env.yaml`.
1. Individua le seguenti righe:

   ```yaml
     deploy:
   ...
       SEARCH_CONFIGURATION:
         engine: opensearch
   ```

1. Se non si dispone di queste righe, aggiungerle al file `.magento.env.yaml`.
1. Se queste righe esistono, **modificare il motore** da *[!DNL opensearch]* a *[!DNL livesearch]*.
1. Esegui il commit della modifica e ridistribuiscila.

## Lettura correlata

* [Installa [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html) nella Guida di Live Search
