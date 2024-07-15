---
title: "MDVA-28763: problemi relativi alla gestione delle immagini dei prodotti tramite API REST"
description: La patch MDVA-28763 risolve diversi problemi relativi alla gestione della raccolta multimediale tramite l'API REST. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5. I problemi sono pianificati per essere risolti nelle versioni successive di Adobe Commerce.
exl-id: 736fbfa8-b6a3-413c-a220-fd772d87ed04
feature: REST, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# MDVA-28763: problemi relativi alla gestione delle immagini dei prodotti tramite API REST

La patch MDVA-28763 risolve diversi problemi relativi alla gestione della raccolta multimediale tramite l&#39;API REST. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5. I problemi sono pianificati per essere risolti nelle versioni successive di Adobe Commerce (vedi le descrizioni dei problemi in [Problemi](#issues).

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce on-premise 2.3.2 - 2.3.3.x
* Adobe Commerce sull’infrastruttura cloud 2.3.2 - 2.3.3.x

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problemi {#issues}

La patch MDVA-28763 include correzioni per i seguenti problemi associati alla raccolta multimediale:

* Quando si utilizza REST API per aggiornare i video di YouTube (`PUT rest/V1/products/ {SKU}`), Adobe Commerce visualizza una miniatura per il video, ma il lettore video non viene caricato quando si fa clic sul pulsante &quot;Riproduci&quot;. Pianificato per essere corretto in Adobe Commerce 2.3.6.
* La chiamata `PUT /V1/products/:sku/media/:entryId` crea una nuova voce anziché sostituire quella esistente. Risolto in Adobe Commerce 2.3.5.
* Problemi relativi all’eliminazione delle immagini del prodotto quando i prodotti vengono assegnati a più visualizzazioni dello store. Risolto in Adobe Commerce 2.3.4.
* I commercianti con più siti web possono ora utilizzare REST per creare e aggiornare i prodotti mantenendo l’ereditarietà dell’immagine e del ruolo dell’immagine. In precedenza, quando un commerciante utilizzava REST per creare e aggiornare i prodotti e un prodotto veniva aggiornato per la visualizzazione store, venivano caricati e salvati i ruoli immagine predefiniti per tale visualizzazione store. Di conseguenza, dopo l’aggiornamento i ruoli immagine store non ereditano più dall’ambito predefinito. Pianificato per essere corretto in Adobe Commerce 2.3.6.
* Attributi multimediali (immagine, miniatura, ecc.) i valori nelle viste store che fanno riferimento a immagini rimosse non vengono puliti automaticamente. Pianificato per essere corretto in Adobe Commerce 2.4.2.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
