---
title: 'PWA Studio: il browser non è in grado di risolvere il sito .local.pwadev'
description: Questo articolo fornisce una soluzione per i casi in cui un altro programma o processo ha modificato il [file host](https://en.wikipedia.org/wiki/Hosts_(file\) e rimosso la voce per il dominio del progetto.
exl-id: a1606016-906a-433f-9e40-9faa5f9bd790
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# PWA Studio: il browser non è in grado di risolvere il sito .local.pwadev

Questo articolo fornisce una soluzione per i casi in cui un altro programma o processo ha modificato il [file host](https://en.wikipedia.org/wiki/Hosts_(file\) e ha rimosso la voce per il dominio del progetto.

## Prodotti e versioni interessati

PWA Studio per Adobe Commerce

## Problema

Quando si esplora il sito di sviluppo/gestione temporanea non è possibile visualizzare il sito `.local.pwadev`.

## Causa

PWA Studio ti consente di assegnare al computer locale un nome host personalizzato e un certificato SSL per il progetto. Ciò comporta la creazione di una nuova voce nel file host del computer con un aspetto simile a `my-storefront-project-abc123.local.pwadev`.

Questa voce comunica a qualsiasi browser sul computer dello sviluppatore di esaminare il progetto storefront locale quando accede a tale URL. Se un altro programma o processo ha rimosso tale voce, il browser non saprà dove andare e non sarà in grado di risolvere il sito `.local.pwadev`.

## Soluzione

È possibile [modificare manualmente il file host](https://support.rackspace.com/how-to/modify-your-hosts-file/) per aggiungere nuovamente la voce, ma è necessario esaminare l&#39;altro software installato per vedere cosa ha sovrascritto la modifica precedente.

## Lettura correlata nella knowledge base del supporto

* [PWA Studi: errore di attendibilità del certificato autofirmato](https://support.magento.com/hc/en-us/articles/360038973172)
* [PWA Studio: Webpack si blocca prima di iniziare la compilazione](/help/troubleshooting/miscellaneous/pwa-studio-webpack-hangs-before-beginning-compilation.md)
* [PWA Studio: nel browser viene visualizzato l’errore &quot;Impossibile eseguire il proxy a&quot;](/help/troubleshooting/miscellaneous/pwa-studio-browser-displays-cannot-proxy-to-error.md)
* [PWA Studio: errori di convalida durante l’esecuzione della modalità sviluppatore](/help/troubleshooting/miscellaneous/pwa-studio-validation-errors-when-running-developer-mode.md)
