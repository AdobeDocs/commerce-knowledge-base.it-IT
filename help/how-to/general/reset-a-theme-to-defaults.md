---
title: Reimpostare un tema sui valori predefiniti
description: A seconda dei problemi che potresti incontrare durante la personalizzazione dei temi e lo sviluppo del tuo store, potresti non avere accesso tramite l’amministratore di Commerce. Puoi cancellare e ripristinare il tema predefinito senza accedere all’amministratore. Dopo aver cancellato il tema, viene applicato il tema Luma predefinito.
exl-id: 86304dd5-f448-4dcc-ad07-04ecc6c85b6d
feature: Cache
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 0%
---
# Reimpostare un tema sui valori predefiniti

A seconda dei problemi che potresti incontrare durante la personalizzazione dei temi e lo sviluppo del tuo store, potresti non avere accesso tramite l’amministratore di Commerce. Puoi cancellare e ripristinare il tema predefinito senza accedere all’amministratore. Dopo aver cancellato il tema, viene applicato il tema Luma predefinito.

Durante lo sviluppo di componenti Adobe Commerce (tutte le implementazioni) e Magento Open Source (moduli, temi e pacchetti di lingue), l’ambiente in rapida evoluzione richiede la cancellazione periodica di determinate directory e cache. In caso contrario, il codice viene eseguito con eccezioni e non funzionerà correttamente. Per informazioni dettagliate, consulta [Cancellare le directory durante lo sviluppo](https://developer.adobe.com/commerce/php/development/components/clear-directories/) nella documentazione per gli sviluppatori.

## Ambiente e tecnologie

* Adobe Commerce on-premise
* Adobe Commerce sull’infrastruttura cloud
* Magento Open Source

## Prerequisiti

* Strumenti di database

## Passaggi

Se devi reimpostare il tema dell’archivio, ma non puoi accedere al pannello Amministratore, puoi reimpostarlo nel database eseguendo le seguenti operazioni:

1. Utilizzare uno strumento di database come [phpMyAdmin](https://experienceleague.adobe.com/it/docs/commerce-operations/installation-guide/prerequisites/optional-software#phpmyadmin) o accedere al database manualmente dalla riga di comando per eseguire la seguente query SQL: `UPDATE core_config_data SET value=NULL WHERE path='design/theme/theme_id'`
1. Cancella le directory seguenti:
   * `pub/static/frontend`
   * `var/view_preprocessing`
   * `var/cache`
   * `var/page_cache`

In questo modo non ci sarà alcun tema impostato sul livello di visualizzazione punto vendita e quando ricarichi le pagine iniziali del negozio, verrà applicato il tema Luma predefinito.

## Informazioni aggiuntive

* [Cancella directory durante lo sviluppo](https://developer.adobe.com/commerce/php/development/components/clear-directories/) nella documentazione per gli sviluppatori
