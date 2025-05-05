---
title: È necessario utilizzare Fastly per un sito Adobe Commerce headless?
description: È necessario utilizzare Fastly per un sito Adobe Commerce headless?
exl-id: d7e07160-6a61-4c03-8f8c-4f879d86ea44
feature: Cache, GraphQL, Compliance
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '319'
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
Consulta [Cloud for Adobe Commerce > Fastly](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/cdn/fastly) nella documentazione per gli sviluppatori.

Tuttavia, molto probabilmente, per utilizzare il certificato SSL dovrai usare Fastly.

Tutti i clienti di Adobe Commerce su infrastruttura cloud ottengono un certificato SSL condiviso da Fastly come parte del piano di abbonamento cloud. L’aggiunta di un proprio certificato SSL a Fastly è un’opzione a pagamento separata e piuttosto costosa. Pertanto, consigliamo vivamente di abilitare Fastly e, almeno, di testarlo negli ambienti di staging e produzione prima di andare &quot;live&quot;, anche per il tuo sito web Adobe Commerce headless.

## Ulteriori informazioni

* [Siti Web headless: qual è il problema con l&#39;architettura disaccoppiata?](https://pantheon.io/blog/headless-websites-whats-big-deal-decoupled-architecture) di [Josh Koenig](https://pantheon.io/team/josh-koenig).
* [Fastly](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/cdn/fastly) nella documentazione per gli sviluppatori.
