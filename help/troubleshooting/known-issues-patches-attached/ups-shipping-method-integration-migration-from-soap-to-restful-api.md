---
title: '[!DNL UPS] migrazione integrazione metodo di spedizione da [!DNL SOAP] a [!DNL RESTful API]'
promoted: true
description: Applicare una patch per gestire [!DNL UPS] migrazione integrazione metodo di spedizione da [!DNL SOAP] a [!DNL RESTful API] per Adobe Commerce 2.4.4 - 2.4.6-pX.
feature: Shipping/Delivery
role: Developer
exl-id: 8ab5d4a8-0155-4b2c-ab67-d0bd2f949a07
source-git-commit: 6694bb1e041e6285f5bd5a05a1c37b7062521f52
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 0%

---

# [!DNL UPS] migrazione integrazione metodo di spedizione da [!DNL SOAP] a [!DNL RESTful API]

>[!NOTE]
>
>Se hai caricato una delle tre patch di questo articolo prima di **6 giugno 2024**: se stai affrontando questo problema a causa del [!DNL Metric System/SI] misurazioni (chilogrammi e centimetri) non utilizzate, è necessario riapplicare una di queste nuove patch aggiornate ora pubblicate in questo articolo per la versione 2.4.4+/2.4.5+/2.4.6+ di Adobe Commerce/Magento Open Source, altrimenti non sarà possibile selezionare [!DNL Metric System/SI] misurazioni di **chilogrammi** e **centimetri** nel [!DNL UPS] metodi di spedizione in **[!DNL Admin configuration]**. Queste nuove patch sono compatibili con le patch rilasciate in precedenza. Questo problema verrà risolto definitivamente nell’ambito della prossima versione di Adobe Commerce 2.4.7-p1 pianificata per **11 giugno 2024**.

>[!NOTE]
>
>Se hai caricato una delle tre patch di questo articolo prima di **10 ottobre 2023**, è necessario riapplicare una di queste patch ora pubblicata in questo articolo per la versione 2.4.4+/2.4.5+/2.4.6+ di Adobe Commerce/Magento Open Source ancora una volta, perché altrimenti non sarà possibile selezionare e configurare [!DNL UPS] metodi di spedizione in **[!DNL Admin configuration]** e dovrai avere tutti abilitati. Queste nuove patch sono compatibili con le patch rilasciate in precedenza.

Questo articolo fornisce una patch per risolvere i problemi relativi a [!DNL United Parcel Service (UPS)] migrazione integrazione metodo di spedizione da [!DNL SOAP] a [!DNL RESTful API] per Adobe Commerce 2.4.4 - 2.4.6-pX.

In base agli ultimi aggiornamenti del [!DNL UPS API] Modello di sicurezza, [!DNL UPS] ha implementato un [!DNL OAuth 2.0] modello di sicurezza per tutti [!DNL APIs] (Ulteriori dettagli sono disponibili nella sezione [[!DNL UPS] Guida alla migrazione della chiave di accesso al portale per sviluppatori](https://developer.ups.com/oauth-developer-guide?loc=en_US&amp;sp_rid=NTA5MzQ1OTE2NjEyS0&amp;sp_mid=72989914)) migliorare la sicurezza generale per ridurre le frodi e migliorare [!DNL API] funzionalità.

Questo cambiamento influisce sulla nostra attuale [!DNL UPS] implementazione dell’integrazione del metodo di spedizione in Adobe Commerce e richiede di correggere l’implementazione corrente e di migrare da [!DNL SOAP API] al [!DNL RESTful API] per supportare [!DNL OAuth 2.0] protocolli di autenticazione.

**A partire da giugno 2024**, gli esercenti Adobe Commerce non saranno in grado di negoziare con il nostro [!DNL UPS] rilasciando questo hotfix, che consente ai commercianti di Adobe Commerce 2.4.4+/2.4.5+/2.4.6+ di migrare all’ultima versione [!DNL UPS REST APIs].

Questo problema verrà risolto nella versione 2.4.7 di Adobe Commerce/Magento Open Source e la correzione verrà inclusa anche nella versione 2.4.7-beta2 di ottobre 2023.

## Prodotti e versioni interessati

Adobe Commerce su infrastruttura cloud e on-premise e Magento Open Source:

* 2.4.4.
* 2,4,4-pX
* 2.4.5.
* 2,4,5-pX
* 2.4.6.
* 2,4,6-pX

## Cause

Il [!DNL UPS] ha rilasciato un [aggiornamento di sicurezza per [!DNL API]](https://developer.ups.com/oauth-developer-guide?loc=en_US&amp;sp_rid=NTA5MzQ1OTE2NjEyS0&amp;sp_mid=72989914).

Se si dispone di Unione europea (altre origini possono sperimentare lo stesso problema) come origine della spedizione, ciò causerà un errore nel [!DNL UPS REST] richiesta: &quot;*Una spedizione non può avere un KGS/IN o LBS/CM o OZS/CM come unità di misura.*&quot;

## Soluzione

Utilizza le seguenti patch allegate, a seconda della versione di Adobe Commerce/Magento Open Source in uso:

Per risolvere il problema nelle versioni 2.4.4+, 2.4.5+ e 2.4.6+, è necessario applicare la patch corrispondente alla versione di Adobe Commerce/Magento Open Source in uso.

## Patch

Utilizza le seguenti patch allegate, a seconda della versione di Adobe Commerce/Magento Open Source in uso:

### Per le versioni 2.4.4, 2.4.4-pX:

* [AC-11984_UPS_Shipping_Method_Migration_REST_API_2.4.4x_COMPOSER.patch.zip](assets/AC-11984_UPS_Shipping_Method_Migration_REST_API_2.4.4x_COMPOSER.patch.zip)

### Per le versioni 2.4.5, 2.4.5-pX:

* [AC-11983_UPS_Shipping_Method_Migration_REST_API_2.4.5x_COMPOSER.patch.zip](assets/AC-11983_UPS_Shipping_Method_Migration_REST_API_2.4.5x_COMPOSER.patch.zip)

### Per le versioni 2.4.6, 2.4.6-pX:

* [AC-11916_UPS_Shipping_Method_Migration_REST_API_2.4.6x_COMPOSER.patch.zip](assets/AC-11916_UPS_Shipping_Method_Migration_REST_API_2.4.6x_COMPOSER.patch.zip)

## Come applicare il cerotto

Decomprimi il file e visualizza [Come applicare una patch del compositore fornita dall&#39;Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) nella knowledge base di supporto per le istruzioni.

## Come stabilire se i cerotti sono stati applicati

Considerando che non è possibile verificare facilmente se il problema è stato corretto, è possibile verificare se la patch è stata applicata correttamente. Questo utilizza (ad esempio: *AC-9363*) come cerotto da controllare.

<u>Per farlo, segui questi passaggi</u>:

1. [Installare [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. Esegui il comando:

   ```bash
   vendor/bin/magento-patches -n status |grep "9363|Status"
   ```

1. Dovresti vedere un output simile a questo, dove AC-9363 restituisce il *Applicato* stato:

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/AC-9363_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```
