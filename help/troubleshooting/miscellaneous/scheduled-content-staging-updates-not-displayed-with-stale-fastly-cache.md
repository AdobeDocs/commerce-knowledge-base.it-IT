---
title: Gli aggiornamenti pianificati per la gestione temporanea dei contenuti non vengono visualizzati con la cache Fastly non aggiornata
description: Questo articolo corregge i casi in cui gli archivi Adobe Commerce non visualizzano gli aggiornamenti pianificati quando si utilizzano Content Staging e Fastly. Il problema è dovuto alla funzione Fastly Soft Purge abilitata per impostazione predefinita. Questa funzione riduce il carico delle risorse dell’applicazione e rigenera una nuova cache solo su una seconda richiesta. Per risolvere il problema, puoi abilitare la pagina Rimuovi CMS tramite l’amministratore Commerce per rigenerare e distribuire sempre nuovo contenuto.
exl-id: becbffaa-b6dd-4e9b-894e-17901c40223a
feature: CMS, Cache, Page Content, Staging
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: ddbd0f6e-b569-5a04-8a70-55058777c373
    internal-label: CMS
  - id: 17d326fa-534a-55a5-b46f-8ae1de1e2f75
    internal-label: Page Content
  - id: 0054e3a7-7067-583b-bfd2-ab39dada9ab5
    internal-label: Staging
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
source-wordcount: '491'
ht-degree: 0%
---
# Gli aggiornamenti pianificati per la gestione temporanea dei contenuti non vengono visualizzati con la cache Fastly non aggiornata

Questo articolo corregge i casi in cui gli archivi Adobe Commerce non visualizzano gli aggiornamenti pianificati quando si utilizzano Content Staging e Fastly. Il problema è dovuto alla funzione Fastly Soft Purge abilitata per impostazione predefinita. Questa funzione riduce il carico delle risorse dell’applicazione e rigenera una nuova cache solo su una seconda richiesta. Per risolvere il problema, puoi abilitare la pagina Rimuovi CMS tramite l’amministratore Commerce per rigenerare e distribuire sempre nuovo contenuto.

## Problema

Aggiornamenti pianificati per una risorsa di contenuto del negozio (pagina, prodotto, blocco, ecc.) non vengono visualizzati nella vetrina subito dopo l&#39;ora di inizio dell&#39;aggiornamento. Ciò si verifica quando gli aggiornamenti sono stati pianificati utilizzando la funzionalità [Gestione temporanea dei contenuti](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html).

## Causa

A causa della funzionalità di eliminazione temporanea di Fastly (attivata per impostazione predefinita), la vetrina Adobe Commerce continua a ricevere il contenuto precedentemente memorizzato nella cache (non aggiornato) quando si invia a Fastly **la prima** richiesta per la risorsa aggiornata. Fastly richiede una seconda richiesta per rigenerare i dati del sito.

Di conseguenza, Fastly può distribuire contenuto non aggiornato fino alla seconda richiesta di contenuto aggiornato.

**Memorizzazione in cache prevista:** Dopo aver pianificato un aggiornamento per una risorsa di contenuto tramite Content Staging, Adobe Commerce invia una richiesta per aggiornare la cache a Fastly. Annulla infine la validità del contenuto precedentemente memorizzato in cache (senza eliminare il contenuto) e inizia a fornire il contenuto aggiornato.

**Memorizzazione in cache effettiva:** Se Fastly fornisce ancora il contenuto non aggiornato quando riceve **la prima** richiesta per il contenuto aggiornato, invierà solo il contenuto rigenerato e corretto dopo aver ricevuto **la seconda** richiesta. Questo comportamento è stato implementato per ridurre il carico del server rinnovando la cache solo in aree con traffico comprovato, senza rigenerare la cache per l’intero sito web. Aggiorna gradualmente la cache, salvando le risorse dell’applicazione.

## Soluzione

Se anche per la prima richiesta non è consentito distribuire contenuto non aggiornato, è possibile disabilitare la funzione di eliminazione temporanea e abilitare la pagina CMS di eliminazione:

1. Accedi al tuo amministratore Commerce locale come amministratore.
1. Vai a **Archivi** > **Configurazione** > **Avanzate** > **Sistema** > **Cache a pagina intera**.
1. Espandere **Fastly Configuration**, quindi espandere **Advanced**.
1. Impostare **Usa eliminazione temporanea** su *No*.
1. Impostare **Rimuovi pagina CMS** su *Sì*.
1. Fai clic su **Salva configurazione** nella parte superiore della pagina.


![purge_options.png](assets/purge_options.png)

## Documentazione correlata

* [Configurare le opzioni di eliminazione](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) nella Guida all&#39;infrastruttura di Commerce su Cloud.
* [Gestione temporanea del contenuto](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html) nella documentazione di contenuto e progettazione.
* [Distribuzione di contenuto non aggiornato](https://docs.fastly.com/guides/performance-tuning/serving-stale-content) nella documentazione Fastly.
