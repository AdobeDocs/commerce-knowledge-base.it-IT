---
title: 'ERRORE: riscaldamento non riuscito in Adobe Commerce sull’infrastruttura cloud'
description: 'Questo articolo fornisce una soluzione per quando la cache delle pagine si sta scaldando e non riesce con un errore:'
exl-id: 20a88030-b1c9-4fdc-83c1-f344d44cd2e1
feature: Cache, Cloud, Paas
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
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
source-wordcount: '213'
ht-degree: 0%
---
# ERRORE: riscaldamento non riuscito in Adobe Commerce sull’infrastruttura cloud

Questo articolo fornisce una soluzione per quando la cache delle pagine si sta scaldando e non riesce con un errore:

*ERRORE: riscaldamento non riuscito:`<website link>`*

## Prodotti e versioni interessati

* Adobe Commerce sull&#39;infrastruttura cloud, tutte le [versioni supportate](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problema

Riscaldamento della cache non riuscito.

<u>Passaggi da riprodurre</u>:

Avviare le operazioni di riscaldamento della cache.

<u>Risultato previsto</u>:

Caricamenti di pagine o dell’intero sito.

<u>Risultato effettivo</u>:

Il sito non è disponibile o il tempo di risposta è troppo alto. *ERRORE: riscaldamento non riuscito:`<website link>`*

## Causa

Il riscaldamento della cache non funziona se è abilitato il controllo degli accessi HTTP.

## Soluzione

Verificare che il controllo degli accessi non sia abilitato: accedere al ramo/ambiente specifico, fare clic sull&#39;icona **Impostazioni** e controllare l&#39;impostazione **Controllo degli accessi HTTP**. In questo caso non è possibile eseguire il riscaldamento della cache e il controllo degli accessi deve essere disabilitato.

## Lettura correlata

* [Guida utente di Adobe Commerce > Cache a pagina intera](https://experienceleague.adobe.com/it/docs/commerce-admin/systems/tools/cache-management#full-page-caching) nella guida utente.
* [Riscaldamento della cache e sito non disponibile in Adobe Commerce](/help/troubleshooting/miscellaneous/cache-warming-up-and-site-unavailable-on-magento.md) nella Knowledge Base di supporto.
