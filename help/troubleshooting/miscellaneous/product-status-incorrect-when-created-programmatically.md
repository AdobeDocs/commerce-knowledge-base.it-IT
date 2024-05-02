---
title: Lo stato del prodotto non è corretto quando viene creato a livello di programmazione
description: Questo articolo corregge i casi in cui lo stato del prodotto è Disattivato e i prodotti non vengono visualizzati nella vetrina o sono assegnati a viste errate, quando vengono creati o aggiornati a livello di programmazione.
exl-id: ac02f961-f9e2-4620-839f-b8dbd0befb15
feature: Products
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 0%

---

# Lo stato del prodotto non è corretto quando viene creato a livello di programmazione

Questo articolo corregge i casi in cui lo stato del prodotto è Disattivato e i prodotti non vengono visualizzati nella vetrina o sono assegnati a viste errate, quando vengono creati o aggiornati a livello di programmazione.

## Prodotti e versioni interessati

* Adobe Commerce sull’infrastruttura cloud 2.X.X
* Adobe Commerce on-premise 2.X.X

## Problema

Quando i prodotti del catalogo vengono creati o aggiornati a livello di programmazione da uno script con l’applicazione Adobe Commerce avviata, i prodotti potrebbero avere lo stato Disabilitato e/o essere assegnati a viste archivio errate.

## Causa

Il problema potrebbe essere dovuto alle restrizioni ACL impostate per i ruoli di amministratore dell’istanza di Adobe Commerce. In caso di applicazione avviata, non vi saranno sessioni di amministrazione inizializzate con le impostazioni ACL appropriate. In questo caso, le convalide nel `Magento_AdminGws` modulo, responsabile del controllo delle autorizzazioni per tali azioni.

## Soluzione per uno stato del prodotto errato

Impostare una preferenza ID dinamica per `Magento\Framework\Authorization\PolicyInterface`, come descritto nella [ObjectManager>Aggiornamenti programmatici dei prodotti](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/object-manager.html#programmatic-product-updates) nella documentazione per gli sviluppatori.

## Lettura correlata

* [Github: impossibile modificare lo stato del prodotto creato con productRepository](https://github.com/magento/magento2/issues/5664)
