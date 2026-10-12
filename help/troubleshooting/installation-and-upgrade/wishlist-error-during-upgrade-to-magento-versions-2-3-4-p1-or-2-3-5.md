---
title: Errore nella lista dei desideri durante l’aggiornamento alle versioni 2.3.4-p1 o 2.3.5 di Adobe Commerce
description: Questo articolo fornisce una correzione del problema noto durante l’aggiornamento alle versioni 2.3.4-p1 e 2.3.5 di Adobe Commerce relativo a un errore della lista dei desideri durante l’aggiornamento a tali versioni.
exl-id: 97479615-bf3f-4544-a9c1-8f19ba74318e
feature: Install, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%
---
# Errore nella lista dei desideri durante l’aggiornamento alle versioni 2.3.4-p1 o 2.3.5 di Adobe Commerce

Questo articolo fornisce una correzione del problema noto durante l’aggiornamento alle versioni 2.3.4-p1 e 2.3.5 di Adobe Commerce relativo a un errore della lista dei desideri durante l’aggiornamento a tali versioni.

## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud 2.3.4-p1 e 2.3.5
* Adobe Commerce on-premise 2.3.4-p1 e 2.3.5

## Problema

Durante l’aggiornamento di Adobe Commerce (tutti i metodi di distribuzione) e Magento Open Source alla versione 2.3.5 o 2.3.4-p1, dal modulo potrebbe venire visualizzato un errore nella lista dei desideri (dettagliato di seguito):

```php
Magento_Wishlist
```

L&#39;aggiornamento da Adobe Commerce (tutti i metodi di distribuzione)/Magneto Open Source versione 2.3.4-p1 **alla versione 2.3.4-p2** o da Adobe Commerce (tutti i metodi di distribuzione)/Magneto Open Source versione 2.3.5 **alla versione 2.3.5-p1** corregge l&#39;errore.

<u>Passaggi da riprodurre</u>:

Aggiorna Adobe Commerce (tutti i metodi di distribuzione)/Magento Open Source alla versione 2.3.4-p1 o 2.3.5.

<u>Risultato previsto</u>:

Il processo di aggiornamento ad Adobe Commerce (tutti i metodi di distribuzione)/Magento Open Source versione 2.3.4-p1 o 2.3.5 viene completato normalmente.

<u>Risultato effettivo</u>:

Durante l’aggiornamento, viene visualizzato il seguente errore:

```php
Module ‘Magento_Wishlist’:

Unable to apply data patch Magento\Wishlist\Setup\Patch\Data\CleanUpData for module Magento_Wishlist. Original exception message: Unable to unserialize value. Error: Syntax error
```

## Soluzioni

* Se stavi effettuando l&#39;aggiornamento ad Adobe Commerce (tutti i metodi di distribuzione)/Magneto Open Source versione 2.3.5, **effettua l&#39;aggiornamento alla versione 2.3.5-p1**. La versione 2.3.5-p1 di Adobe Commerce (tutti i metodi di distribuzione)/Magento Open Source sostituisce la versione 2.3.5.
* Se stavi effettuando l&#39;aggiornamento ad Adobe Commerce (tutti i metodi di distribuzione)/Magento Open Source versione 2.3.4-p1, **effettua l&#39;aggiornamento alla versione 2.3.4-p2**. Adobe Commerce (tutti i metodi di distribuzione)/Magneto Open Source versione 2.3.4-p2 sostituisce la versione 2.3.4-p1.

## Lettura correlata

Nella documentazione per gli sviluppatori:

* [Guida di Adobe Commerce sull’infrastruttura cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/overview)
* [Adobe Commerce sull’infrastruttura cloud: aggiornamento della versione di Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version)
* [Adobe Commerce on-premise e Magento Open Source: aggiornamento dell’applicazione e dei moduli Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/overview)
* [Pagina di configurazione voce elenco desideri](https://developer.adobe.com/commerce/frontend-core/guide/layouts/product-layouts#wishlist-item-configure-page)
* [Moduli per la generazione di rapporti avanzati](https://developer.adobe.com/commerce/php/development/advanced-reporting/modules/)
