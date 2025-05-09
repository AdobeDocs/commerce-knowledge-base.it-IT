---
title: Errore nella lista dei desideri durante l’aggiornamento alle versioni 2.3.4-p1 o 2.3.5 di Adobe Commerce
description: Questo articolo fornisce una correzione del problema noto durante l’aggiornamento alle versioni 2.3.4-p1 e 2.3.5 di Adobe Commerce relativo a un errore della lista dei desideri durante l’aggiornamento a tali versioni.
exl-id: 97479615-bf3f-4544-a9c1-8f19ba74318e
feature: Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# Errore nella lista dei desideri durante l’aggiornamento alle versioni 2.3.4-p1 o 2.3.5 di Adobe Commerce

Questo articolo fornisce una correzione del problema noto durante l’aggiornamento alle versioni 2.3.4-p1 e 2.3.5 di Adobe Commerce relativo a un errore della lista dei desideri durante l’aggiornamento a tali versioni.

## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud 2.3.4-p1 e 2.3.5
* Adobe Commerce on-premise 2.3.4-p1 e 2.3.5

## Problema

Quando aggiorni Adobe Commerce (tutti i metodi di distribuzione) e il Magento Open Source alla versione 2.3.5 o 2.3.4-p1, dal modulo puoi visualizzare un errore nella lista dei desideri (dettagliato di seguito):

```php
Magento_Wishlist
```

L&#39;aggiornamento da Adobe Commerce (tutti i metodi di distribuzione)/Magneto Open Source versione 2.3.4-p1 **alla versione 2.3.4-p2** o da Adobe Commerce (tutti i metodi di distribuzione)/Magneto Open Source versione 2.3.5 **alla versione 2.3.5-p1** corregge l&#39;errore.

<u>Passaggi da riprodurre</u>:

Aggiorna il Magento Open Source/Adobe Commerce (tutti i metodi di distribuzione) alla versione 2.3.4-p1 o 2.3.5.

<u>Risultato previsto</u>:

Il processo di aggiornamento ad Adobe Commerce (tutti i metodi di distribuzione)/Magento Open Source versione 2.3.4-p1 o 2.3.5 viene completato normalmente.

<u>Risultato effettivo</u>:

Durante l’aggiornamento, viene visualizzato il seguente errore:

```php
Module ‘Magento_Wishlist’:

Unable to apply data patch Magento\Wishlist\Setup\Patch\Data\CleanUpData for module Magento_Wishlist. Original exception message: Unable to unserialize value. Error: Syntax error
```

## Soluzioni

* Se stavi effettuando l&#39;aggiornamento ad Adobe Commerce (tutti i metodi di distribuzione)/Magneto Open Source versione 2.3.5, **effettua l&#39;aggiornamento alla versione 2.3.5-p1**. La versione 2.3.5-p1 di Adobe Commerce (tutti i metodi di implementazione)/Magento Open Source sostituisce la versione 2.3.5.
* Se stavi effettuando l&#39;aggiornamento ad Adobe Commerce (tutti i metodi di distribuzione)/Magento Open Source versione 2.3.4-p1, **effettua l&#39;aggiornamento alla versione 2.3.4-p2**. Adobe Commerce (tutti i metodi di distribuzione)/Magneto Open Source versione 2.3.4-p2 sostituisce la versione 2.3.4-p1.

## Lettura correlata

Nella documentazione per gli sviluppatori:

* [Guida di Adobe Commerce sull&#39;infrastruttura cloud](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/overview)
* [Adobe Commerce sull&#39;infrastruttura cloud - Aggiornamento della versione di Adobe Commerce](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version)
* [Adobe Commerce on-premise e Magento Open Source - Aggiornamento dell&#39;applicazione Adobe Commerce e dei moduli](https://experienceleague.adobe.com/it/docs/commerce-operations/upgrade-guide/overview)
* [Pagina di configurazione elemento lista dei desideri](https://developer.adobe.com/commerce/frontend-core/guide/layouts/product-layouts/#wishlist-item-configure-page)
* [Moduli che forniscono funzioni di reporting avanzate](https://developer.adobe.com/commerce/php/development/advanced-reporting/modules/)
