---
title: Gli script personalizzati lato server non vengono eseguiti nella directory dei file multimediali del pub
description: Questo articolo fornisce una correzione per i casi in cui gli script personalizzati lato server non vengono eseguiti se inseriti nel "./pub/media/` della tua applicazione Adobe Commerce sull’infrastruttura cloud. Si tratta di una limitazione di sicurezza prevista, poiché il ".La directory /pub/media/` è scrivibile. Per rendere eseguibili gli script, inserirli in directory non scrivibili, ad esempio `./app/code/` o `./pub/`.
exl-id: fcad8a5d-47d6-4729-93a4-2410d7710d69
feature: Media
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Gli script personalizzati lato server non vengono eseguiti nella directory dei file multimediali del pub

Questo articolo fornisce una correzione per i casi in cui gli script personalizzati lato server non vengono eseguiti se inseriti nel `./pub/media/` dell’applicazione Adobe Commerce sull’infrastruttura cloud. Si tratta di una limitazione di sicurezza prevista, in quanto `./pub/media/` directory scrivibile. Per rendere eseguibili gli script, inserirli in directory non scrivibili, ad esempio `./app/code/` o `./pub/`.

## Versioni interessate

* Adobe Commerce su infrastruttura cloud: versione 2.1.x e successive, Starter e Pro pianificano architettura, Wings e architetture legacy

## Problema: script non eseguiti

Non è possibile eseguire gli script personalizzati lato server quando vengono avviati.

Ad esempio, quando l’utente finale (acquirente Adobe Commerce) fa clic sul collegamento che porta al `\*.php` file con lo script (come *domain.com/media/directory/script.php* ), lo script viene scaricato anziché eseguito.

## Causa: percorso non corretto del file di script

Il problema si verifica quando i file di script si trovano in `./pub/media/` directory dell’applicazione Adobe Commerce sull’infrastruttura cloud. Si tratta di un comportamento previsto: a causa di limitazioni di sicurezza, i file delle directory scrivibili (`./pub/media/`) non vengono mai eseguite.

## Soluzione: inserire script in directory non scrivibili

Memorizzare gli script lato server in directory non scrivibili, ad esempio `./app/code/` o `./pub/`  &quot;

## Documentazione correlata

* [Cloud for Adobe Commerce > Struttura del progetto > Directory scrivibili](https://devdocs.magento.com/guides/v2.3/cloud/project/project-start.html#write-dir) nella documentazione per gli sviluppatori.
