---
title: '''[!UICONTROL Recommendations] [!DNL JS] errori dopo l’aggiornamento alla versione 2.4.5 di Adobe Commerce'
description: Questo articolo corregge alcuni casi in cui, dopo l’aggiornamento ad Adobe Commerce (tutti i metodi di distribuzione), [!DNL JS] errori nella console relativi al prodotto [!UICONTROL Recommendations] moduli.
feature: Install, Upgrade
role: Developer
exl-id: 51d899eb-48f7-48c5-8bda-bd72a4d28945
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%

---

# [!UICONTROL Recommendations] [!DNL JS] errori dopo l’aggiornamento alla versione 2.4.5 di Adobe Commerce

Questo articolo corregge alcuni casi in cui, dopo l’aggiornamento ad Adobe Commerce (tutti i metodi di distribuzione), [!DNL JS] errori nella console relativi al prodotto [!UICONTROL Recommendations] moduli/unità.

Non è attualmente previsto di risolvere questo problema nelle versioni future.

## Versioni e prodotti interessati

* Adobe Commerce (tutti i metodi di distribuzione) durante l’aggiornamento alla versione 2.4.5

## Problema

Il problema è causato dalla pagina web storefront che fa ancora riferimento ad alcuni prodotti eliminati [!UICONTROL Recommendations] moduli/unità (blocchi e/o widget) nella propria home page [!DNL CMS].

<u>Passaggi da riprodurre</u>:

1. Esegui l’aggiornamento ad Adobe Commerce 2.4.5.
1. Accedi alla pagina web vetrina.
1. Fare clic con il pulsante destro del mouse e selezionare **Inspect** per aprire web inspector nel browser.
1. Fai clic su **[!UICONTROL Console]** scheda.
1. Rivedi [!DNL JS] errori.

<u>Risultati previsti</u>:

Aggiornamento riuscito senza [!DNL JS] errori.

<u>Risultati effettivi</u>:

Diversi tipi di [!DNL JS] gli errori vengono visualizzati nella console del browser web.

## Soluzione alternativa

Come soluzione alternativa, puoi esaminare tutte le [!UICONTROL Recommendations] unità utilizzate nella pagina e rimuovete eventuali unità eliminate.
