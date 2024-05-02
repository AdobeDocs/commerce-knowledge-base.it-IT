---
title: Verifica la patch per il problema Adobe Commerce con lo strumento Quality Patches
description: Questo articolo fornisce una panoramica dello strumento Quality Patches (QPT) e collegamenti alle risorse che spiegano come utilizzarlo.
exl-id: 43393708-3939-449f-a764-b2ac6326165f
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# Verifica la patch per il problema Adobe Commerce con lo strumento Quality Patches

Questo articolo fornisce una panoramica dello strumento Quality Patches (QPT) e collegamenti alle risorse che spiegano come utilizzarlo.

## Prodotti e versioni interessati

* Adobe Commerce on-premise [versioni supportate](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)
* Adobe Commerce su infrastruttura cloud, tutto [versioni supportate](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Che cosa sono le patch di qualità

Il [Strumento Patch di qualità](https://github.com/magento/quality-patches) (QPT) sono patch individuali sviluppate da Adobe e dalla community del Magento Open Source.

Consente di:

* applicare le patch di qualità incluse nella confezione
* ripristinare le patch applicate in precedenza
* visualizzare le informazioni generali sulle patch di qualità disponibili per la versione installata di Adobe Commerce.

Di seguito è riportato un esempio della tabella di stato che consente di visualizzare le patch disponibili:

![Elenco_patch_Magento](assets/status_table.png)

Lo strumento ha lo scopo di consentire l’utilizzo autonomo di patch per problemi che potresti riscontrare con Adobe Commerce o di applicare facilmente patch suggerite dal supporto Adobe Commerce.

>[!NOTE]
>
>QPT è solo per patch di qualità. Le patch di sicurezza sono disponibili nel [Centro sicurezza di Magento](https://magento.com/security/patches).

## Patch disponibili nello strumento Patch di qualità

Fare riferimento a [Strumento Patch di qualità](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori per l’elenco delle patch disponibili.

## Come installare e utilizzare lo strumento Quality Patches

I comandi di installazione e utilizzo sono diversi per Adobe Commerce on-premise e Adobe Commerce sull’infrastruttura cloud, perché per il cloud il pacchetto QPT è incluso nel pacchetto degli strumenti ece.

### Come installare e utilizzare QPT per Adobe Commerce on-premise

Fare riferimento a [Guida all&#39;aggiornamento del software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori per informazioni dettagliate su come installare e utilizzare QPT per l’applicazione e il ripristino delle patch.

### Come installare e utilizzare QPT per Adobe Commerce sull’infrastruttura cloud

Fare riferimento a [Cloud for Adobe Commerce > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori per informazioni dettagliate su come installare e utilizzare QPT per applicare e ripristinare le patch su Adobe Commerce nell’infrastruttura cloud.

## Lettura correlata

* [Note sulla versione dello strumento Patch di qualità](https://devdocs.magento.com/quality-patches/release-notes.html) nella documentazione per gli sviluppatori.
* [Come applicare le patch del compositore fornite dall&#39;Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) nella nostra knowledge base di supporto.
