---
title: "Adobe Commerce 2.4.1: pagina vuota al salvataggio del modulo dotdigital Page Builder"
description: Questo articolo fornisce una soluzione alternativa per un problema noto in Adobe Commerce 2.4.1 relativo alla visualizzazione di una pagina web vuota dopo il salvataggio di un modulo con Page Builder digitale nel pannello di amministrazione quando si utilizza il browser Safari.
exl-id: 682eac73-1ad2-4093-acfb-6a8da4c05cf5
feature: Page Builder
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---

# Adobe Commerce 2.4.1: pagina vuota al salvataggio del modulo per il Page Builder dotdigital

Questo articolo fornisce una soluzione alternativa per un problema noto in Adobe Commerce 2.4.1 relativo alla visualizzazione di una pagina web vuota dopo il salvataggio di un modulo con Page Builder digitale nel pannello di amministrazione quando si utilizza il browser Safari.

## Prodotti e versioni interessati

* Adobe Commerce on-premise 2.4.1
* Adobe Commerce sull’infrastruttura cloud 2.4.1

## Problema

<u>Passaggi da riprodurre</u>

1. Vai a **Admin Panel** > **Content** > **Pages** e seleziona **Edit** di qualsiasi pagina.
1. Vai a **Contenuto** e fai clic sul pulsante **Modifica con Page Builder**.
1. Trascina il blocco **modulo digitale** e seleziona **Modifica**.
1. Seleziona uno dei moduli di test, quindi scegli la modalità **Incorporato** e salva il modulo.
1. Salva la modifica della pagina.

<u>Risultato previsto:</u>

Salvataggio della pagina Web completato.

<u>Risultato effettivo:</u>

La pagina Web è vuota. Dopo aver ricaricato la pagina Web, le modifiche vengono applicate.

## Soluzione alternativa

La soluzione consiste nell’utilizzare un browser alternativo a Safari. Il problema è pianificato per essere risolto nella prossima versione, Adobe Commerce 2.4.2, nel primo trimestre del 2021.

## Lettura correlata

* [Cos&#39;è Page Builder?](https://developer.adobe.com/commerce/frontend-core/page-builder/) nella documentazione per gli sviluppatori.
* [Configurazione di Page Builder](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/setup.html?lang=it) nella documentazione per gli sviluppatori.
* [Page Builder](https://experienceleague.adobe.com/it/docs/commerce-admin/page-builder/introduction) nella guida utente.
* [Page Builder - Elementi](https://experienceleague.adobe.com/it/docs/commerce-admin/page-builder/workspace#elements) nella guida utente.
