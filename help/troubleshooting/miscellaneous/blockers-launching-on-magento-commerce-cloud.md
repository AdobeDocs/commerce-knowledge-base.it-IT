---
title: Blocchi all’avvio su Adobe Commerce per l’infrastruttura cloud
description: Questo articolo fornisce una correzione per i blocchi da avviare sull’infrastruttura cloud di Adobe Commerce, inclusi i problemi relativi a configurazione Fastly, certificati SSL, reindirizzamenti 301 e prestazioni delle risorse statiche.
exl-id: 3b2c331f-5d90-4051-ada1-4934538fce79
feature: Cache, Cloud, Marketing Tools, Observability, Paas
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
  - id: 4239b8a6-e74f-567d-a7a5-b98b9ead0ea4
    internal-label: Observability
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 0%
---
# Blocchi all’avvio su Adobe Commerce per l’infrastruttura cloud

Questo articolo fornisce una correzione per i blocchi da avviare sull’infrastruttura cloud di Adobe Commerce, inclusi i problemi relativi a configurazione Fastly, certificati SSL, reindirizzamenti 301 e prestazioni delle risorse statiche.

## &#x200B;1. Configurazione rapida

[Fastly](https://www.fastly.com/) è una rete CDN (Content Delivery Network) basata su vernice per la distribuzione di risorse statiche. È necessario per Adobe Commerce sull’infrastruttura cloud negli ambienti di produzione, quindi è importante configurare Fastly e testare il tuo sito web (UAT) con Fastly abilitato e configurato, sia negli ambienti di staging che in quelli di produzione.

>[!WARNING]
>
>Con la cache a pagina intera abilitata (FPC), le prestazioni del sito web sono diverse; assicurati di verificarle prima di andare &quot;live&quot;.

Il processo di configurazione Fastly è documentato in dettaglio nell&#39;argomento [Configura Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=it) nella nostra guida utente. Di seguito sono riportati i passaggi importanti.

### 1 bis. Verificare di avere installato la versione più recente del modulo Fastly

Per ottenere le funzioni e i miglioramenti più recenti, accertati di aver installato la versione più recente del modulo Fastly. Per verificare se disponi della versione più recente di Fastly, controlla [Aggiorna il modulo Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=it#upgrade-the-fastly-module) nella nostra guida utente. Per ulteriori dettagli, consulta [Configura Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=it) nella nostra guida utente.

### 1 ter. Abilitare e configurare Fastly tramite l’amministratore di Commerce

Per ulteriori dettagli, consulta [Ottieni le tue credenziali Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=it#get-fastly-credentials) nella nostra guida utente.

### 1 quater. Carica snippet VCL Fastly

Per ulteriori dettagli, consulta [Caricare VCL in Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=it) nella nostra guida utente.

È inoltre possibile [creare e aggiungere snippet VCL personalizzati](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html?lang=it).

### 1 quinquies. Configurare DNS per Fastly


Consulta questo articolo per i passaggi dettagliati: [Configura Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=it#update-dns-configuration-with-development-settings) nella nostra guida utente.

## &#x200B;2. Certificato SSL (TLS) valido

Problema: senza un certificato SSL valido e funzionante, non è possibile verificare i metodi di pagamento esterno nella pagina Pagamento nell&#39;ambiente di staging.

Consiglio **:** Richiedi il certificato SSL condiviso per i nomi di dominio di gestione temporanea o Live.


## &#x200B;3. Configurare e testare i reindirizzamenti 301

Problema: i reindirizzamenti 301 non sono forniti o sono configurati in modo errato, causando il calo delle classificazioni SEO (Search Engine Optimization) e delle inserzioni di ricerca.

Consiglio **:** Configurare e testare con attenzione i reindirizzamenti 301.

Nel caso in cui stai eseguendo la migrazione da un vecchio sito Web a uno nuovo, i reindirizzamenti 301 conducono i clienti dalle vecchie pagine precedentemente indicizzate alle pagine corrette del nuovo store, come segue:

http://www.mywebsite.com/old-category-page.html **>** http://www.mywebsite.com/new-seo-friendly-category-page.html

**Articoli correlati:**

* [Reindirizza tramite route.yaml](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/routes/redirects.html?lang=it) nella guida utente.
* [Reindirizzamenti tramite Cloud Console](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=it) nella guida utente.
* [L&#39;URL riscrive](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/url-rewrites/url-rewrite.html?lang=it) nella nostra guida utente.

## &#x200B;4. Prestazioni risorsa

Problema: le risorse statiche vengono distribuite lentamente, pertanto le prestazioni del sito sono scarse (tempi di caricamento lunghi, contenuti multimediali non visualizzati, ecc.). Le risorse statiche del sito web sono risorse CSS, immagini, video, documenti allegati e molto altro. Il modo in cui vengono organizzati e serviti è un fattore chiave nelle prestazioni del sito.

Consiglio: per identificare le possibili cause di prestazioni scadenti, utilizzare [Adobe Commerce Performance Toolkit](https://github.com/magento/magento2/tree/2.3/setup/performance-toolkit) per il test delle prestazioni. Puoi inoltre considerare questi strumenti di terze parti:

* [Assedio](https://www.joedog.org/siege): utilità di benchmark e test di carico HTTP; supporta l&#39;autenticazione di base, i cookie, i protocolli HTTP, HTTPS e FTP.
* [Jmeter](https://jmeter.apache.org/): uno strumento affidabile per il test di carico e la misurazione delle prestazioni. Consente di misurare le prestazioni per il traffico con picchi di traffico, ad esempio per le vendite flash.
* [New Relic](https://support.newrelic.com/): individua i processi e le aree del sito causando un rallentamento delle prestazioni con tempo di rilevamento trascorso per azione, come la trasmissione di dati, query, Redis e così via.
* [WebPageTest](https://www.webpagetest.org/) (gratuito) e [PKingdom](https://www.pingdom.com/) (a pagamento): l&#39;analisi in tempo reale delle pagine del sito viene caricata con percorsi di origine diversi.

Puoi anche prendere in considerazione [minimizzazione](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html?lang=it) per CSS, JavaScript e HTML.

**Articoli correlati:**

* [Verifica distribuzione](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production.html?lang=it) nella documentazione per gli sviluppatori.
