---
title: laminas/laminas-escape 2.7.1 causa un errore nelle pagine Adobe Commerce frontend e Admin
description: Questo articolo fornisce una soluzione per il problema in cui il rilascio di laminas/laminas-escape:2.7.1 interrompe la funzionalità di Adobe Commerce nella gestione dei prodotti, nelle categorie e nelle pagine dei prodotti. Questo problema verrà risolto in Adobe Commerce 2.4.3.
exl-id: 89de6827-7b90-4f08-92fb-56ed31ae2672
feature: Admin Workspace, Categories
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# laminas/laminas-escape 2.7.1 causa un errore nelle pagine Adobe Commerce frontend e Admin


## Prodotti e versioni interessati

* Adobe Commerce sulla nostra architettura cloud 2.3.5+
* Adobe Commerce 2.3.5+

## Problema

Dopo l&#39;aggiornamento a laminas/laminas-escape:2.7.1 nella pagina viene visualizzato un messaggio di errore.

<u>Passaggi da riprodurre</u>:

Aggiornare laminas/laminas-escape alla versione 2.7.1.

<u>Risultato previsto</u>:

Nessun errore.

<u>Risultato effettivo</u>:

Dopo l&#39;aggiornamento a laminas/laminas-escape:2.7.1, sulla pagina di modifica del prodotto (o di gestione del prodotto) viene visualizzato un messaggio di errore: *TypeError: rawurlencode() prevede che il parametro 1 sia una stringa, int specificato in /var/www/magento/vendor/laminas/laminas-escaper/src/Escaper.php:246*
Questo errore si verifica sulle pagine front-end e Admin causando la distorsione del contenuto della pagina.

## Causa

laminas/laminas-escape 2.7.1 ha iniziato a utilizzare la convalida rigorosa del tipo per la classe Escaper.

## Soluzione

Esegui `composer require laminas/laminas-escaper:2.7.0` nella directory principale di ciascun progetto.

## Lettura correlata

Documentazione laminas: [Fuga laminare](https://docs.laminas.dev/laminas-escaper/)
