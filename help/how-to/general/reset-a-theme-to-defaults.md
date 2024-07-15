---
title: Reimpostare un tema sui valori predefiniti
description: A seconda dei problemi che potresti incontrare durante la personalizzazione dei temi e lo sviluppo del tuo store, potresti non avere accesso tramite l’amministratore di Commerce. Puoi cancellare e ripristinare il tema predefinito senza accedere all’amministratore. Dopo aver cancellato il tema, viene applicato il tema Luma predefinito.
exl-id: 86304dd5-f448-4dcc-ad07-04ecc6c85b6d
feature: Cache
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Reimpostare un tema sui valori predefiniti

A seconda dei problemi che potresti incontrare durante la personalizzazione dei temi e lo sviluppo del tuo store, potresti non avere accesso tramite l’amministratore di Commerce. Puoi cancellare e ripristinare il tema predefinito senza accedere all’amministratore. Dopo aver cancellato il tema, viene applicato il tema Luma predefinito.

Durante lo sviluppo di Adobe Commerce (tutte le implementazioni) e dei componenti di Magento Open Source (moduli, temi e pacchetti di lingue), l’ambiente in rapida evoluzione richiede la cancellazione periodica di determinate directory e cache. In caso contrario, il codice viene eseguito con eccezioni e non funzionerà correttamente. Per informazioni dettagliate, consulta [Cancellare le directory durante lo sviluppo](https://devdocs.magento.com/guides/v2.2/howdoi/php/php_clear-dirs.html) nella documentazione per gli sviluppatori.

## Ambiente e tecnologie

* Adobe Commerce on-premise
* Adobe Commerce sull’infrastruttura cloud
* Magento Open Source

## Prerequisiti

* Strumenti di database

## Passaggi

Se devi reimpostare il tema dell’archivio, ma non puoi accedere al pannello Amministratore, puoi reimpostarlo nel database eseguendo le seguenti operazioni:

1. Utilizzare uno strumento di database come [phpMyAdmin](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/optional.html#install-optional-phpmyadmin) o accedere al database manualmente dalla riga di comando per eseguire la seguente query SQL: `UPDATE core_config_data SET value=NULL WHERE path='design/theme/theme_id'`
1. Cancella le directory seguenti:
   * `pub/static/frontend`
   * `var/view_preprocessing`
   * `var/cache`
   * `var/page_cache`

In questo modo non ci sarà alcun tema impostato sul livello di visualizzazione punto vendita e quando ricarichi le pagine iniziali del negozio, verrà applicato il tema Luma predefinito.

## Informazioni aggiuntive

* [Cancella directory durante lo sviluppo](https://devdocs.magento.com/guides/v2.2/howdoi/php/php_clear-dirs.html) nella documentazione per gli sviluppatori
