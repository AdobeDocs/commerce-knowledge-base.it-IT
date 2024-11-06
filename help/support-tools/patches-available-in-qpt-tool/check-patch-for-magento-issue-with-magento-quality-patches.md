---
title: Verifica la patch per il problema Adobe Commerce con lo strumento Quality Patches
description: Questo articolo fornisce una panoramica dello strumento Quality Patches (QPT) e collegamenti alle risorse che spiegano come utilizzarlo.
exl-id: 43393708-3939-449f-a764-b2ac6326165f
feature: Tools and External Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# Verifica la patch per il problema Adobe Commerce con lo strumento Quality Patches

Questo articolo fornisce una panoramica dello strumento Quality Patches (QPT) e collegamenti alle risorse che spiegano come utilizzarlo.

## Prodotti e versioni interessati

* Adobe Commerce on-premise, tutte le [versioni supportate](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)
* Adobe Commerce sull&#39;infrastruttura cloud, tutte le [versioni supportate](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Che cosa sono le patch di qualità

Lo [strumento Patch di qualità](https://github.com/magento/quality-patches) (QPT) è costituito da singole patch sviluppate da Adobe e dalla community del Magento Open Source.

Consente di:

* applicare le patch di qualità incluse nella confezione
* ripristinare le patch applicate in precedenza
* visualizzare le informazioni generali sulle patch di qualità disponibili per la versione installata di Adobe Commerce.

Di seguito è riportato un esempio della tabella di stato che consente di visualizzare le patch disponibili:

![elenco_patch_Magento](assets/status_table.png)

Lo strumento ha lo scopo di consentire l’utilizzo autonomo di patch per problemi che potresti riscontrare con Adobe Commerce o di applicare facilmente patch suggerite dal supporto Adobe Commerce.

>[!NOTE]
>
>QPT è solo per patch di qualità. Le patch di sicurezza sono disponibili in [Centro sicurezza PC di Magento](https://magento.com/security/patches).

## Patch disponibili nello strumento Patch di qualità

Per un elenco delle patch disponibili, consultare [Strumento Patch di qualità](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella documentazione per gli sviluppatori.

## Come installare e utilizzare lo strumento Quality Patches

I comandi di installazione e utilizzo sono diversi per Adobe Commerce on-premise e Adobe Commerce sull’infrastruttura cloud, perché per il cloud il pacchetto QPT è incluso nel pacchetto degli strumenti ece.

### Come installare e utilizzare QPT per Adobe Commerce on-premise

Per informazioni dettagliate su come installare e utilizzare il QPT per l&#39;applicazione e il ripristino delle patch, consultare la [Guida all&#39;aggiornamento software > Applicazione delle patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.

### Come installare e utilizzare QPT per Adobe Commerce sull’infrastruttura cloud

Consulta [Cloud for Adobe Commerce > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori per informazioni dettagliate su come installare e utilizzare QPT per applicare e ripristinare le patch su Adobe Commerce nell&#39;infrastruttura cloud.

## Lettura correlata

* [Note sulla versione dello strumento Patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/release-notes) nella documentazione per gli sviluppatori.
* [Come applicare le patch del compositore fornite da Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) nella Knowledge Base di supporto.
