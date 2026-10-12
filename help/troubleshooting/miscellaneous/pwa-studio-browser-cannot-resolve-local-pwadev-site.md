---
title: 'PWA Studio: impossibile risolvere il sito .local.pwadev nel browser'
description: Questo articolo fornisce una soluzione per i casi in cui un altro programma o processo ha modificato il [file host] (https://en.wikipedia.org/wiki/Hosts_(file\) e rimosso la voce per il dominio del progetto.
exl-id: a1606016-906a-433f-9e40-9faa5f9bd790
feature: Configuration
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%
---
# PWA Studio: impossibile risolvere il sito .local.pwadev nel browser

Questo articolo fornisce una soluzione per i casi in cui un altro programma o processo ha modificato il [file host]&#x200B;(https://en.wikipedia.org/wiki/Hosts_(file\) e ha rimosso la voce per il dominio del progetto.

## Prodotti e versioni interessati

PWA Studio per Adobe Commerce

## Problema

Quando si esplora il sito di sviluppo/gestione temporanea non è possibile visualizzare il sito `.local.pwadev`.

## Causa

PWA Studio ti consente di assegnare al computer locale un nome host personalizzato e un certificato SSL per il progetto. Ciò comporta la creazione di una nuova voce nel file host del computer con un aspetto simile a `my-storefront-project-abc123.local.pwadev`.

Questa voce comunica a qualsiasi browser sul computer dello sviluppatore di esaminare il progetto storefront locale quando accede a tale URL. Se un altro programma o processo ha rimosso tale voce, il browser non saprà dove andare e non sarà in grado di risolvere il sito `.local.pwadev`.

## Soluzione

È possibile [modificare manualmente il file host](https://docs.rackspace.com/docs/modify-your-hosts-file) per aggiungere nuovamente la voce, ma è necessario esaminare l&#39;altro software installato per vedere cosa ha sovrascritto la modifica precedente.

## Lettura correlata nella knowledge base del supporto

* [PWA Studio: errore di attendibilità del certificato autofirmato](https://support.magento.com/hc/en-us/articles/360038973172)
* [PWA Studio: Webpack si blocca prima di iniziare la compilazione](/help/troubleshooting/miscellaneous/pwa-studio-webpack-hangs-before-beginning-compilation.md)
* [PWA Studio: nel browser viene visualizzato l’errore &quot;Impossibile eseguire il proxy a&quot;](/help/troubleshooting/miscellaneous/pwa-studio-browser-displays-cannot-proxy-to-error.md)
* [PWA Studio: errori di convalida durante l’esecuzione della modalità sviluppatore](/help/troubleshooting/miscellaneous/pwa-studio-validation-errors-when-running-developer-mode.md)
