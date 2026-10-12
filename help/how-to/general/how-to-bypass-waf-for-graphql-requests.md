---
title: Come evitare le richieste di WAF per GraphQL
description: Questo articolo spiega come evitare WAF per le richieste GraphQL.
feature: GraphQL
exl-id: 3a0f2c22-f976-4596-b6a9-4634be1ea4c3
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 0%
---
# Come evitare le richieste di WAF per GraphQL

In questo articolo viene illustrato come ignorare le richieste WAF per GraphQL quando il WAF [!DNL Fastly] blocca le richieste GraphQL.

## Prodotti e versioni interessati

Adobe Commerce su infrastruttura cloud (tutte le versioni)

## Causa

A causa della natura intrinseca delle richieste GraphQL, possono essere presenti molti caratteri ripetuti che possono attivare il blocco falso positivo delle richieste da parte del WAF [!DNL Fastly].

## Soluzione

1. Ignora il WAF per queste richieste aggiungendo uno snippet personalizzato tramite il modulo [!DNL Fastly] di Magento:

   tipo: recv
   priorità: 15
   contenuto:

   ```
   if( req.url.path ~ "^/graphql" ) {
       set req.http.bypasswaf = "1";
   }
   ```

1. Fai clic su **[!UICONTROL Upload VCL to Fastly]**.

## Lettura correlata

* [Firewall applicazione Web (WAF)](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-waf-service) nella guida di Commerce su infrastruttura cloud.
* [Guida introduttiva a VCL personalizzato](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets) nella guida Commerce su infrastruttura cloud.
