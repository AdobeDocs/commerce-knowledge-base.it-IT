---
title: Le modifiche .magento.env.yaml non vengono visualizzate in env.php dopo la distribuzione
description: Questo articolo fornisce una soluzione per il problema in cui le modifiche nel file .magento.env.yaml non vengono riportate in app/etc/env.php dopo la distribuzione.
exl-id: 39ea7295-ba5a-40cc-bc68-a5e0b965c1a7
feature: Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# Le modifiche .magento.env.yaml non vengono visualizzate in env.php dopo la distribuzione

>[!NOTE]
>
>Se hai questo problema, effettua l’aggiornamento a ece-tools 2002.1.5 per correggerlo. 2002.1.5 dispone della funzionalità di ripristino di opcache in ogni distribuzione, pertanto non è mai necessario modificare l&#39;impostazione `opcache.enable_cli=1`. Se non desideri eseguire l’aggiornamento, è necessario eseguire i passaggi della soluzione alternativa come descritto di seguito nella soluzione.

Questo articolo fornisce una soluzione per il problema in cui le modifiche in `.magento.env.yaml` file non riflessi in `app/etc/env.php` dopo la distribuzione.

## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud (tutti [versioni supportate](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)).

## Problema

Modifiche apportate in `.magento.env.yaml` non influiscono sul `app/etc/env.php` generato.

<u>Passaggi da riprodurre:</u>

Modifica qualsiasi valore in `.magento.env.yaml` e invia al server, dove deve definire la configurazione (e le impostazioni di distribuzione) per l’ambiente attualmente estratto. Per i passaggi, consulta [Variabili di ambiente > Distribuisci variabili](https://devdocs.magento.com/cloud/env/variables-deploy.html) nella documentazione per gli sviluppatori.

<u>Risultato previsto:</u>

Modifiche apportate in `.magento.env.yaml` influire sul `app/etc/env.php` generato.

<u>Risultato effettivo:</u>

Le modifiche non hanno alcun effetto sul `app/etc/env.php` variabili dopo la distribuzione.

## Causa

Il problema potrebbe essere causato dal valore errato del `opcache.enable_cli` parametro in `php.ini` file.

## Soluzione

1. Verificare che il sistema sia configurato in base a [Best practice per le prestazioni di Adobe Commerce > Consigli software](https://devdocs.magento.com/guides/v2.4/performance-best-practices/software.html).
1. Controlla se `opcache.enable_cli` direttiva in `php.ini` è impostato su `0` eseguendo: `php -i | grep opcache.enable_cli`
1. Se l’output si presenta come `opcache.enable_cli=1` , modifica il `php.ini` nella directory principale del progetto e modificare `opcache.enable_cli=1` a `opcache.enable_cli=0`
1. Ridistribuisci il progetto.

## Lettura correlata

* [Cloud for Adobe Commerce > Genera e implementa](https://devdocs.magento.com/cloud/project/magento-env-yaml.html).
