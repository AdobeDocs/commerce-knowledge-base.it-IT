---
title: "BB2B-2598: aggiunge la funzionalità di caching per storeConfig, currency, country, countries, availableStores GraphQl queries"
description: Applica la patch BB2B-2598 per aggiungere la funzionalità di caching alle query GraphQl storeConfig, currency, country, countries e availableStores.
exl-id: 37551954-d721-4f3a-b237-cd795f715a5f
feature: B2B, GraphQL, Cache
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# BB2B-2598: aggiunge la funzionalità di caching a `storeConfig`, `currency`, `country`, `countries`, e `availableStores` Query GraphQl

La patch BB2B-2598 aggiunge la funzionalità di caching a `storeConfig`, `currency`, `country`, `countries`, e `availableStores` Query GraphQl. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30. L’ID della patch è BB2B-2598. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7-beta1.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

`availableStores`, `countries`, `country`, `currency`, `storeConfig`, e `customAttributeMetadata` Le query GraphQL non sono memorizzabili in cache.

<u>Prerequisiti</u>:

* Il server punta a [!DNL Varnish] trasferimento al backend Adobe Commerce.
* Impostazione di configurazione `system/full_page_cache/caching_application` è impostato su *2* ([!DNL Varnish]), oppure vai su Adobe Commerce Admin > **[!UICONTROL Stores]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Caching Application]** > e impostarlo su [!DNL Varnish].

Dopo aver applicato la patch, esegui i passaggi seguenti per assicurarti che la funzionalità di caching sia ora disponibile:

1. Invia `GET` richiesta a una qualsiasi delle query GraphQL elencate sopra, utilizzando qualsiasi campo arbitrario.
1. Invia di nuovo la richiesta senza modifiche; noterai che è molto più veloce. La richiesta non viene inviata al backend ma è completamente gestita da [!DNL Varnish] come hit della cache.
1. Se sono necessarie ulteriori prove, aggiungi un commento alla disattivazione di `X-Magento-Debug` intestazione presente nel nostro [VCL](https://github.com/magento/magento2/blob/026e5b29a5edfd619bbdea62d636b3cab2ea03b4/app/code/Magento/PageCache/etc/varnish6.vcl#L227), quindi riavvia [!DNL Varnish] ed esegui nuovamente i passaggi precedenti.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
