---
title: Lo stato del prodotto non è corretto quando viene creato a livello di programmazione
description: Questo articolo corregge i casi in cui lo stato del prodotto è Disattivato e i prodotti non vengono visualizzati nella vetrina o sono assegnati a viste errate, quando vengono creati o aggiornati a livello di programmazione.
exl-id: ac02f961-f9e2-4620-839f-b8dbd0befb15
feature: Products
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '227'
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

Il problema potrebbe essere dovuto alle restrizioni ACL impostate per i ruoli di amministratore dell’istanza di Adobe Commerce. In caso di applicazione avviata, non vi saranno sessioni di amministrazione inizializzate con le impostazioni ACL appropriate. In questo caso, le convalide non riusciranno nel modulo `Magento_AdminGws`, che è responsabile del controllo delle autorizzazioni per tali azioni.

## Soluzione per uno stato del prodotto errato

Impostare una preferenza ID dinamica per `Magento\Framework\Authorization\PolicyInterface`, come descritto nell&#39;argomento [ObjectManager>Aggiornamenti del prodotto a livello di programmazione](https://developer.adobe.com/commerce/php/development/components/object-manager/) nella documentazione per gli sviluppatori.

## Lettura correlata

* [Github: impossibile modificare lo stato del prodotto creato con productRepository](https://github.com/magento/magento2/issues/5664)
