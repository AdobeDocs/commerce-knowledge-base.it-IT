---
title: '[!DNL Advanced Reporting] Errore 404 in Adobe Commerce'
description: Questo articolo fornisce una patch per il problema di Adobe Commerce quando un commerciante riceve un errore 404 quando tenta di accedere a [[!DNL Advanced Reporting]](https://experienceleague.adobe.com/docs/commerce-admin/config/general/advanced-reporting.html). Dopo l'installazione della patch, gli utenti potranno accedere [!DNL Advanced Reporting].
exl-id: bac61704-44fe-4bd2-b342-af90219231ef
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# [!DNL Advanced Reporting] Errore 404 in Adobe Commerce

Questo articolo fornisce una patch per il problema di Adobe Commerce quando un commerciante riceve un errore 404 quando tenta di accedere [[!DNL Advanced Reporting]](https://experienceleague.adobe.com/docs/commerce-admin/config/general/advanced-reporting.html). Dopo l&#39;installazione della patch, gli utenti potranno accedere [!DNL Advanced Reporting].

Per verificare se questa patch è in grado di risolvere il problema, esaminare innanzitutto i registri utilizzando il comando seguente:

`zgrep analytics_collect_data var/log/support_report.log var/log/support_report.log.1.gz`

Se vedi il `Not valid cipher` errore, applica la patch allegata.

## Prodotti e versioni interessati

Adobe Commerce 2.2.6

## Problema

Un commerciante riceve un errore 404 quando tenta di accedere a [!DNL Advanced Reporting].

## Soluzione

Per risolvere il problema, applica la patch allegata a questo articolo. Per scaricarlo, scorri verso il basso fino alla fine dell’articolo e fai clic sul nome del file, oppure fai clic sul seguente collegamento: [Scarica MDVA-18980\_EE\_2.2.6\_COMPOSER\_v1](assets/MDVA-18980_EE_2.2.6_COMPOSER_v1.patch.zip)

## Come applicare il cerotto

Consulta [Come applicare una patch del compositore fornita dall&#39;Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) per istruzioni.

## File allegati
