---
title: '''[!UICONTROL salesRule] problemi di etichette durante l''aggiornamento dalle versioni &lt; 2.4.5'''
description: Applica una patch per risolvere i problemi **[!UICONTROL salesRule]** durante l'aggiornamento da Adobe Commerce versioni &lt; 2.4.5.
exl-id: e1bd6d44-576e-4d91-bab5-32c41e3b8300
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# **[!UICONTROL salesRule]** problemi di etichette durante l&#39;aggiornamento dalle versioni &lt; 2.4.5

La funzionalità di gestione temporanea delle etichette **[!UICONTROL salesRule]** è stata introdotta in Adobe Commerce [2.4.5](/docs/commerce-operations/release/notes/adobe-commerce/2-4-5.html). La modifica potrebbe potenzialmente causare problemi durante l’aggiornamento da Adobe Commerce &lt; 2.4.5 a qualsiasi versione >= 2.4.5. Dopo l&#39;aggiornamento, è possibile che **[!UICONTROL salesRule]** etichette non corrispondano correttamente. Per risolvere il problema, applicare una patch subito dopo l’aggiornamento a una versione più recente di Adobe Commerce.

## Prodotti e versioni interessati

Adobe Commerce su infrastruttura cloud &lt; 2.4.5

## Patch

Utilizzi la seguente patch allegata:

[ACSD-50625_2.4.5-P1.patch.zip](assets/ACSD-50625_2.4.5-p1.patch.zip)

## Come applicare il cerotto

1. Segui i passaggi in [Esegui un aggiornamento](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html?lang=it) nella guida di Commerce.
1. Applicare la patch allegata prima della fase **[!UICONTROL Update metadata]**.
(Puoi anche applicare la patch dopo aver completato la fase **[!UICONTROL Update metadata]**, ma in questo caso devi eseguire di nuovo `bin/magento setup:upgrade`).
1. Procedi con gli altri passaggi in [Esegui un aggiornamento](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html?lang=it).
