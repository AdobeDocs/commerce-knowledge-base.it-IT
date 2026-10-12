---
title: È necessario utilizzare Fastly per un sito Adobe Commerce headless?
description: È necessario utilizzare Fastly per un sito Adobe Commerce headless?
exl-id: d7e07160-6a61-4c03-8f8c-4f879d86ea44
feature: Cache, GraphQL, Compliance
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
    internal-label: Compliance
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%
---
# È necessario utilizzare Fastly per un sito Adobe Commerce headless?

>[!NOTE]
>
>Tutti i clienti devono utilizzare Fastly per gli ambienti di produzione e staging. Fastly è una rete CDN (Content Delivery Network) che fornisce memorizzazione nella cache di pagine complete, ottimizzazione delle immagini e servizi di sicurezza (DDoS e WAF) come parte dei progetti Adobe Commerce su infrastrutture cloud. Si tratta di componenti core della soluzione Adobe Commerce che offrono prestazioni e sicurezza migliori. Queste funzioni fanno parte della conformità PCI di Adobe. È necessario impostare questi servizi Fastly negli ambienti di Starter Master, Staging, Pro Staging e Produzione. Se utilizzi Adobe Commerce in una distribuzione headless, tutto il traffico API proveniente da Internet pubblico deve passare attraverso Fastly e si consiglia vivamente di utilizzare Fastly per memorizzare nella cache le risposte GraphQL. Consulta [Guida per gli sviluppatori di GraphQL > Memorizzazione in cache con Fastly](https://developer.adobe.com/commerce/webapi/graphql/usage/caching/#caching-with-fastly) nella documentazione per gli sviluppatori.

## **Domanda**

Sto sviluppando un’implementazione headless di Adobe Commerce. Devo ancora utilizzare Fastly come servizio CDN per esso?

## **Risposta**

No, non è vero. In questa situazione, puoi saltare utilizzando Fastly - almeno, all’inizio dello sviluppo.

L’unica situazione che potresti non abilitare è una distribuzione headless.
Consulta [Cloud for Adobe Commerce > Fastly](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly) nella documentazione per gli sviluppatori.

Tuttavia, molto probabilmente, per utilizzare il certificato SSL dovrai usare Fastly.

Tutti i clienti di Adobe Commerce su infrastruttura cloud ottengono un certificato SSL condiviso da Fastly come parte del piano di abbonamento cloud. L’aggiunta di un proprio certificato SSL a Fastly è un’opzione a pagamento separata e piuttosto costosa. Pertanto, consigliamo vivamente di abilitare Fastly e, almeno, di testarlo negli ambienti di staging e produzione prima di andare &quot;live&quot;, anche per il tuo sito web Adobe Commerce headless.

## Ulteriori informazioni

* [Siti Web headless: qual è il problema con l&#39;architettura disaccoppiata?](https://pantheon.io/blog/headless-websites-whats-big-deal-decoupled-architecture) di [Josh Koenig](https://pantheon.io/team/josh-koenig).
* [Fastly](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly) nella documentazione per gli sviluppatori.
