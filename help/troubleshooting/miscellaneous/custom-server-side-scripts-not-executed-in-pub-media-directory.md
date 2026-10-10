---
title: Gli script personalizzati lato server non vengono eseguiti nella directory dei file multimediali del pub
description: Questo articolo fornisce una correzione per i casi in cui gli script personalizzati lato server non vengono eseguiti se inseriti nella directory "./pub/media/" dell’applicazione Adobe Commerce sull’infrastruttura cloud. Si tratta di una limitazione di sicurezza prevista, poiché la directory "./pub/media/" è scrivibile. Per rendere eseguibili gli script, inseriscili in directory non scrivibili, ad esempio `./app/code/` o `./pub/`.
exl-id: fcad8a5d-47d6-4729-93a4-2410d7710d69
feature: Media
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4ca54350-01cb-5b22-8966-5f2873dc6d90
    internal-label: Media
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 0%
---
# Gli script personalizzati lato server non vengono eseguiti nella directory dei file multimediali del pub

Questo articolo fornisce una correzione per i casi in cui gli script personalizzati lato server non vengono eseguiti se inseriti nella directory `./pub/media/` dell&#39;applicazione Adobe Commerce nell&#39;infrastruttura cloud. Si tratta di una limitazione di sicurezza prevista, poiché la directory `./pub/media/` è scrivibile. Per rendere eseguibili gli script, inserirli in directory non scrivibili, ad esempio `./app/code/` o `./pub/`.

## Versioni interessate

* Adobe Commerce su infrastruttura cloud: versione 2.1.x e successive, Starter e Pro pianificano architettura, Wings e architetture legacy

## Problema: script non eseguiti

Non è possibile eseguire gli script personalizzati lato server quando vengono avviati.

Ad esempio, quando l&#39;utente finale (acquirente Adobe Commerce) fa clic sul collegamento che porta al file `\*.php` con lo script (come *domain.com/media/directory/script.php* ), lo script viene scaricato anziché eseguito.

## Causa: percorso non corretto del file di script

Il problema si verifica quando i file di script si trovano nella directory `./pub/media/` dell&#39;applicazione Adobe Commerce nell&#39;infrastruttura cloud. Si tratta di un comportamento previsto: a causa di limitazioni di sicurezza, i file delle directory scrivibili (`./pub/media/`) non vengono mai eseguiti.

## Soluzione: inserire script in directory non scrivibili

Archiviare gli script lato server in directory non scrivibili, ad esempio `./app/code/` o `./pub/` &quot;

## Documentazione correlata

* [Cloud for Adobe Commerce > Struttura del progetto > Directory scrivibili](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/project/file-structure#writable-directories) nella documentazione per gli sviluppatori.
