---
title: '''**[!UICONTROL salesRules]Problemi relativi alle etichette di ** durante l’aggiornamento dalle versioni < 2.4.5’'
description: Applicare una patch per gestire il **[!UICONTROL salesRules]Problemi di ** durante l’aggiornamento dalle versioni < 2.4.5 di Adobe Commerce.
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# **[!UICONTROL salesRules]** problemi di etichette durante l’aggiornamento dalle versioni &lt; 2.4.5

Il **[!UICONTROL salesRules]** la funzionalità di staging delle etichette è stata introdotta in Adobe Commerce [2.4.5.](/docs/commerce-operations/release/notes/adobe-commerce/2-4-5.html). La modifica potrebbe potenzialmente causare problemi durante l’aggiornamento da Adobe Commerce &lt; 2.4.5 a qualsiasi versione >= 2.4.5. Dopo l’aggiornamento, esiste la possibilità che **[!UICONTROL salesRules]** le etichette non corrispondono. Per risolvere il problema, applicare una patch subito dopo l’aggiornamento a una versione più recente di Adobe Commerce.

## Prodotti e versioni interessati

Adobe Commerce su infrastruttura cloud &lt; 2.4.5

## Patch

Utilizzi la seguente patch allegata:

[ACSD-50625_2.4.5-P1.patch.zip](assets/ACSD-50625_2.4.5-p1.patch.zip)

## Come applicare il cerotto

1. Segui i passaggi descritti in [Eseguire un aggiornamento](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html) nella guida di Commerce.
1. Applicare la patch allegata prima di **[!UICONTROL Update metadata]** fase.
(La patch può essere applicata anche dopo aver completato **[!UICONTROL Update metadata]** ma poi devi eseguire `bin/magento setup:upgrade` ancora).
1. Procedi con gli altri passaggi in [Eseguire un aggiornamento](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html).
