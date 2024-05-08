---
title: Come evitare WAF per le richieste GraphQL
description: Questo articolo spiega come evitare WAF per le richieste GraphQL.
feature: GraphQL
source-git-commit: c35d4ba82fbe1657756e160a73fd575c736b4e1c
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# Come evitare WAF per le richieste GraphQL

Questo articolo spiega come evitare WAF per le richieste GraphQL quando [!DNL Fastly] WAF blocca le richieste GraphQL.

## Prodotti e versioni interessati

Adobe Commerce su infrastruttura cloud (tutte le versioni)

## Causa

A causa della natura intrinseca delle richieste di GraphQL, possono esserci molti caratteri ripetuti che possono attivare il blocco falso positivo delle richieste da parte di [!DNL Fastly] WAF.

## Soluzione

1. Per ignorare il file WAF per queste richieste, aggiungi uno snippet personalizzato attraverso il file [!DNL Fastly] Modulo Magento:

   tipo: recv priority: 15 content:

   ```
   if( req.url.path ~ "^/graphql" ) {
       set req.http.bypasswaf = "1";
   }
   ```

1. Fai clic su **[!UICONTROL Upload VCL to Fastly]**.

## Lettura correlata

* [Firewall applicazione Web (WAF)](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-waf-service) nella guida di Commerce on Cloud Infrastructure.
* [Guida introduttiva a VCL personalizzato](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets) nella guida di Commerce on Cloud Infrastructure.

