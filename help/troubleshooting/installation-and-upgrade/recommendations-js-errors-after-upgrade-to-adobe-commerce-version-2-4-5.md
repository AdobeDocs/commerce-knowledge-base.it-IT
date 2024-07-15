---
title: '''[!UICONTROL Recommendations] [!DNL JS] errori dopo l''aggiornamento ad Adobe Commerce versione 2.4.5'''
description: In questo articolo viene fornita una correzione per i casi in cui, dopo l'aggiornamento ad Adobe Commerce (tutti i metodi di distribuzione), nella console siano presenti  [!DNL JS]  errori relativi ai moduli [!UICONTROL Recommendations] del prodotto.
feature: Install, Upgrade
role: Developer
exl-id: 51d899eb-48f7-48c5-8bda-bd72a4d28945
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%

---

# [!UICONTROL Recommendations] [!DNL JS] errori dopo l&#39;aggiornamento ad Adobe Commerce versione 2.4.5

Questo articolo fornisce una correzione per i casi in cui, dopo l&#39;aggiornamento ad Adobe Commerce (tutti i metodi di distribuzione), nella console siano presenti [!DNL JS] errori relativi ai moduli/unità [!UICONTROL Recommendations] del prodotto.

Non è attualmente previsto di risolvere questo problema nelle versioni future.

## Versioni e prodotti interessati

* Adobe Commerce (tutti i metodi di distribuzione) durante l’aggiornamento alla versione 2.4.5

## Problema

Il problema è causato dal fatto che la pagina Web storefront fa ancora riferimento ad alcuni moduli/unità (blocchi e/o widget) del prodotto eliminato nella relativa home page [!DNL CMS].[!UICONTROL Recommendations]

<u>Passaggi da riprodurre</u>:

1. Esegui l’aggiornamento ad Adobe Commerce 2.4.5.
1. Accedi alla pagina web vetrina.
1. Fai clic con il pulsante destro del mouse e seleziona **Inspect** per aprire il controllo Web nel browser.
1. Fare clic sulla scheda **[!UICONTROL Console]**.
1. Esaminare gli errori [!DNL JS].

<u>Risultati previsti</u>:

Aggiornamento riuscito senza errori [!DNL JS].

<u>Risultati effettivi</u>:

Diversi tipi di errori [!DNL JS] vengono visualizzati nella console del browser Web.

## Soluzione alternativa

Come soluzione alternativa, è possibile esaminare tutte le [!UICONTROL Recommendations] unità utilizzate nella pagina e rimuovere eventuali unità eliminate.
