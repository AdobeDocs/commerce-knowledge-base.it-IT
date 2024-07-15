---
title: Prestazioni lente, esecuzione lenta e cronica prolungata
description: Questo articolo descrive come risolvere i problemi di prestazioni del sito e rallentare l’esecuzione e il blocco di nodi causati dall’attivazione di tabelle a nastro e indicizzatori.
exl-id: a78ca3c3-85b4-40a1-a693-4703dd3ef4b5
feature: Best Practices, Cache, Categories, Catalog Management
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# Prestazioni lente, esecuzione lenta e cronica prolungata

>[!WARNING]
>
>Su qualsiasi versione di Adobe Commerce, poiché alcune estensioni funzionano solo con le tabelle a comparsa, esiste un rischio se si disattivano le tabelle a comparsa. Se si è certi di disporre di alcune estensioni che utilizzano indici Flat Catalog, potrebbe essere necessario tenerne conto quando si impostano tali valori su &quot; *No* &quot;.

In questo articolo viene descritto come risolvere i problemi di prestazioni del sito e rallentare l&#39;esecuzione e il blocco di nodi causati dall&#39;attivazione di [tabelle flat e indicizzatori](https://docs.magento.com/m2/ce/user_guide/catalog/catalog-flat.html).

PRODOTTI E VERSIONI INTERESSATI

* Adobe Commerce su infrastruttura cloud 2.1.x e versioni successive
* Adobe Commerce on-premise 2.1.x e successive
* Magento Open Source 2.1.x e versioni successive

## Problema

Gli indicizzatori piatti possono causare:

* Gravi problemi di carico SQL e di prestazioni del sito.
* Cronisti a lungo in corsa e bloccati.

## Causa

Tabelle semplici e indicizzatori abilitati.

## Soluzione {#solution}

A partire da Adobe Commerce e dal Magento Open Source 2.1.x e versioni successive, l’utilizzo di un catalogo flat non è più una best practice e non è consigliato. L’utilizzo continuo di questa funzione può causare il deterioramento delle prestazioni e altri problemi di indicizzazione. Per disattivare il catalogo flat:

1. In Amministrazione, passa a **Archivi** > **Impostazioni** > **Configurazione**.
1. Nel pannello a sinistra in **Catalogo** , scegli **Catalogo**.
1. Espandere la sezione **Storefront** ed eseguire le operazioni seguenti:
   * Imposta **Usa categoria catalogo flat** su *No*.
   * Imposta **Usa prodotto catalogo flat** su *No*.
1. Al termine, fare clic su **Salva configurazione**. Quando richiesto, aggiorna la cache.
1. Svuota la cache eseguendo `php bin/magento cache:flush`.

Se non è possibile modificare **Usa categoria catalogo flat** e **Usa prodotto catalogo flat** in *No* perché le opzioni sono disattivate, disabilitare gli indicizzatori flat in `app/etc/config.php`:

1. Eseguire questo comando per assicurarsi che tutti gli indicizzatori siano impostati su Aggiorna in base alla pianificazione: `php bin/magento indexer:set-mode schedule`.
1. Modifica `app/etc/config.php` e individua le righe con `flat_catalog_product` e `flat_catalog_category`. Modificale da 1 a 0 per disabilitarle.
1. Esegui il comando `php bin/magento app:config:import`
1. Eseguire questo comando per verificare che gli indici flat siano disabilitati: `php        bin/magento indexer:status`.
1. Svuota la cache eseguendo `php bin/magento cache:flush`.

## Informazioni correlate

[Reimposta manualmente i processi Adobe Commerce cron bloccati su Cloud](/help/how-to/general/reset-stuck-magento-cron-jobs-manually-on-cloud.md) nella knowledge base di supporto.
