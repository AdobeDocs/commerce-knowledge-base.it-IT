---
title: Come evitare WAF per le richieste GraphQL
description: Questo articolo spiega come evitare WAF per le richieste GraphQL.
feature: GraphQL
exl-id: 3a0f2c22-f976-4596-b6a9-4634be1ea4c3
source-git-commit: 2bec86818336a9ef4d8316e257a0ca4256cdd93c
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# Come evitare WAF per le richieste GraphQL

In questo articolo viene illustrato come ignorare WAF per le richieste GraphQL quando WAF [!DNL Fastly] blocca le richieste GraphQL.

## Prodotti e versioni interessati

Adobe Commerce su infrastruttura cloud (tutte le versioni)

## Causa

A causa della natura intrinseca delle richieste GraphQL, possono essere presenti molti caratteri ripetuti che possono attivare il blocco falso positivo delle richieste da parte del WAF [!DNL Fastly].

## Soluzione

1. Ignorare WAF per queste richieste aggiungendo uno snippet personalizzato tramite il modulo di Magento [!DNL Fastly]:

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

* [Web Application Firewall (WAF)](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-waf-service) nella guida di Commerce on Cloud Infrastructure.
* [Guida introduttiva a VCL personalizzato](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets) nella guida Commerce su infrastruttura cloud.
