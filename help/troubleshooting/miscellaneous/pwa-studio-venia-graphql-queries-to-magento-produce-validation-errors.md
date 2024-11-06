---
title: "PWA Studio: le query Venia GraphQL in Adobe Commerce generano errori di convalida"
description: Questo articolo fornisce consigli su come risolvere il problema in cui le query Venia storefront GraphQL nell’istanza Adobe Commerce producono errori di convalida.
exl-id: ba268945-2a10-4af5-8089-cde21f0687bd
feature: GraphQL
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# PWA Studio: le query di Venia GraphQL su Adobe Commerce generano errori di convalida

Questo articolo fornisce consigli su come risolvere il problema in cui le query Venia storefront GraphQL nell’istanza Adobe Commerce producono errori di convalida.

## Prodotti e versioni interessati

* Adobe Commerce on-premise 2.2.x, 2.3.x
* Adobe Commerce sull’infrastruttura cloud 2.2.x, 2.3.x
* Progetto PWA Studio per Adobe Commerce

## Problema

Le query di Venia GraphQL su Adobe Commerce on-premise o Adobe Commerce su infrastrutture cloud generano errori di convalida.

## Causa

Uno dei motivi del problema potrebbe essere la mancata sincronizzazione di Venia e delle relative query GraphQL con lo schema dell’istanza Adobe Commerce connessa.

## Soluzione

Per verificare se le query sono aggiornate, esegui il comando seguente nella directory principale del progetto:

```bash
yarn run validate-queries
```

Verrà visualizzato un rapporto di compatibilità. Se riscontri incompatibilità, devi aggiornare l’istanza PWA Studio o Adobe Commerce. Controlla la [matrice di compatibilità di Adobe Commerce](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/version-compatibility/) per vedere esattamente le versioni necessarie.

Per istruzioni su come effettuare l’aggiornamento, consulta la seguente documentazione:

* Per gli aggiornamenti di PWA Studio, cercare la sezione &quot;Aggiornamento da una versione precedente&quot; delle [note sulla versione di PWA](https://github.com/magento/pwa-studio/releases/) per la versione da aggiornare.
* [Aggiorna Adobe Commerce sulla versione infrastruttura cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) nella documentazione per gli sviluppatori
* [Aggiorna Adobe Commerce on-premise (installato utilizzando &quot;compositore create-project&quot; o archivio)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade) nella documentazione per gli sviluppatori
* [Aggiorna Adobe Commerce on-premise (installato clonando l&#39;archivio Adobe Commerce)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/developer/git-installs) nella documentazione per sviluppatori

## Lettura correlata

* [PWA Studi: Webpack si blocca prima di iniziare la compilazione](/help/troubleshooting/miscellaneous/pwa-studio-webpack-hangs-before-beginning-compilation.md) nella Knowledge Base di supporto
* [PWA Studi: errori di convalida durante l&#39;esecuzione della modalità sviluppatore](/help/troubleshooting/miscellaneous/pwa-studio-validation-errors-when-running-developer-mode.md) nella Knowledge Base di supporto
* [PWA Studi: nel browser viene visualizzato l&#39;errore &quot;Impossibile eseguire il proxy a&quot;](/help/troubleshooting/miscellaneous/pwa-studio-browser-displays-cannot-proxy-to-error.md) nella Knowledge Base del supporto tecnico
* [Configura NPM per poter utilizzare PWA Studio](/help/how-to/general/configure-npm-to-be-able-to-use-pwa-studio.md) nella Knowledge Base di supporto
* [PWA per la documentazione di Adobe Commerce](https://magento.github.io/pwa-studio/)
