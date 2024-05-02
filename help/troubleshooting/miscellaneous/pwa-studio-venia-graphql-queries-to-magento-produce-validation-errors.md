---
title: "PWA Studio: le query Venia GraphQL in Adobe Commerce generano errori di convalida"
description: Questo articolo fornisce consigli su come risolvere il problema in cui le query Venia storefront GraphQL nell’istanza Adobe Commerce producono errori di convalida.
exl-id: ba268945-2a10-4af5-8089-cde21f0687bd
feature: GraphQL
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# PWA Studi: le query di Venia GraphQL su Adobe Commerce generano errori di convalida

Questo articolo fornisce consigli su come risolvere il problema in cui le query Venia storefront GraphQL nell’istanza Adobe Commerce producono errori di convalida.

## Prodotti e versioni interessati

* Adobe Commerce on-premise 2.2.x, 2.3.x
* Adobe Commerce sull’infrastruttura cloud 2.2.x, 2.3.x
* Progetto PWA Studi per Adobe Commerce

## Problema

Le query di Venia GraphQL su Adobe Commerce on-premise o Adobe Commerce su infrastrutture cloud generano errori di convalida.

## Causa

Uno dei motivi del problema potrebbe essere la mancata sincronizzazione di Venia e delle relative query GraphQL con lo schema dell’istanza Adobe Commerce connessa.

## Soluzione

Per verificare se le query sono aggiornate, esegui il comando seguente nella directory principale del progetto:

```bash
yarn run validate-queries
```

Verrà visualizzato un rapporto di compatibilità. Se riscontri incompatibilità, devi aggiornare l’istanza PWA Studi o Adobe Commerce. Controlla la [Matrice di compatibilità per Adobe Commerce](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/version-compatibility/) per visualizzare esattamente le versioni necessarie.

Per istruzioni su come effettuare l’aggiornamento, consulta la seguente documentazione:

* Per gli aggiornamenti di PWA Studi, cerca la sezione &quot;Aggiornamento da una versione precedente&quot; del [Note sulla versione di PWA](https://github.com/magento/pwa-studio/releases/) per la versione da aggiornare a.
* [Aggiornamento della versione di Adobe Commerce sull’infrastruttura cloud](https://devdocs.magento.com/cloud/project/project-upgrade.html) nella documentazione per gli sviluppatori
* [Aggiornamento di Adobe Commerce on-premise (installato utilizzando &quot;compositore create-project&quot; o archivio)](https://devdocs.magento.com/guides/v2.3/comp-mgr/cli/cli-upgrade.html) nella documentazione per gli sviluppatori
* [Aggiornare Adobe Commerce on-premise (installato clonando l’archivio Adobe Commerce)](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/dev_update-magento.html) nella documentazione per gli sviluppatori

## Lettura correlata

* [PWA Studio: Webpack si blocca prima di iniziare la compilazione](/help/troubleshooting/miscellaneous/pwa-studio-webpack-hangs-before-beginning-compilation.md) nella knowledge base di supporto
* [PWA Studi: errori di convalida durante l’esecuzione della modalità sviluppatore](/help/troubleshooting/miscellaneous/pwa-studio-validation-errors-when-running-developer-mode.md) nella knowledge base di supporto
* [PWA Studi: nel browser viene visualizzato l’errore &quot;Impossibile eseguire il proxy su&quot;](/help/troubleshooting/miscellaneous/pwa-studio-browser-displays-cannot-proxy-to-error.md) nella knowledge base di supporto
* [Configurare NPM per l&#39;utilizzo di PWA Studi](/help/how-to/general/configure-npm-to-be-able-to-use-pwa-studio.md) nella knowledge base di supporto
* [Documentazione di PWA per Adobe Commerce](https://magento.github.io/pwa-studio/)
