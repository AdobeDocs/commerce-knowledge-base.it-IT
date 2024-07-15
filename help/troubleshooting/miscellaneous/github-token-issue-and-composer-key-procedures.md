---
title: Problema del token Github e procedure chiave del compositore
description: Questo articolo fornisce soluzioni per il problema di distribuzioni non riuscite relative a errori del token Github causati da chiavi Composer obsolete.
exl-id: 202cb936-f9ba-49ea-bf0a-6e6994d2337a
feature: Identity Management
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# Problema del token Github e procedure chiave del compositore

Questo articolo fornisce soluzioni per il problema di distribuzioni non riuscite relative a errori del token Github causati da chiavi Composer obsolete.

## Prodotti e versioni interessati

* Adobe Commerce sull&#39;infrastruttura cloud, [tutte le versioni supportate](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)
* Compositore versioni 1.10.20 e inferiori

>[!NOTE]
>
>Gli esercenti on-premise di Adobe Commerce devono verificare con il proprio provider di host di utilizzare Composer versione 1.10.21 o successiva a causa delle modifiche al formato del token introdotte da Git.

## Problema

Le distribuzioni non riescono e i registri di distribuzione contengono informazioni simili alle seguenti:

*Errore irreversibile: UnexpectedValueException non rilevata. Il token oauth github per github.com contiene caratteri non validi: &quot;ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx&quot; in /app/vendor/composer/composer/src/Composer/IO/BaseIO.php:129*

## Causa

Le chiavi del compositore obsolete causano errori del token Github che causano distribuzioni non riuscite.

## Soluzione

Per risolvere il problema, aggiorna la versione del Compositore al 1.10.22:

1. Nell&#39;ambiente locale, eseguire `composer require “composer/composer”:”>1.10.21`.
1. Questo aggiunge il requisito per la versione del pacchetto Compositore. Controllare il file di blocco - la versione `composer/composer` deve essere 1.0.22 o successiva.
1. Eseguire il commit di `composer.json` e `composer.lock` e inviare una distribuzione push.

Se questo metodo non funziona, [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

## Lettura correlata

* [Blog Github: dietro i nuovi formati dei token di autenticazione di GitHub](https://github.blog/2021-04-05-behind-githubs-new-authentication-token-formats/)
* [InfoQ.com news article: GitHub cambia il formato del token per migliorare l&#39;identificabilità, la scansione segreta e l&#39;entropia](https://www.infoq.com/news/2021/04/github-new-token-format/)
