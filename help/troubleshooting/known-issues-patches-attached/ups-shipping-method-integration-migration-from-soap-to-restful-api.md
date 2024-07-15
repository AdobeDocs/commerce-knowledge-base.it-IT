---
title: Migrazione dell'integrazione del metodo di spedizione '[!DNL UPS] da [!DNL SOAP] a [!DNL RESTful API]'
promoted: true
description: Applica una patch per gestire la migrazione dell'integrazione del metodo di spedizione  [!DNL UPS] da [!DNL SOAP] a [!DNL RESTful API] per Adobe Commerce 2.4.4 - 2.4.6-pX.
feature: Shipping/Delivery
role: Developer
exl-id: 8ab5d4a8-0155-4b2c-ab67-d0bd2f949a07
source-git-commit: 6694bb1e041e6285f5bd5a05a1c37b7062521f52
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 0%

---

# Migrazione dell&#39;integrazione del metodo di spedizione [!DNL UPS] da [!DNL SOAP] a [!DNL RESTful API]

>[!NOTE]
>
>Se hai caricato una delle tre patch di questo articolo prima del **6 giugno 2024**: se stai affrontando questo problema a causa delle [!DNL Metric System/SI] misurazioni (chilogrammi e centimetri) non utilizzate, devi riapplicare una di queste nuove patch aggiornate ora pubblicate in questo articolo per la tua versione 2.4.4+/2.4.5+/2.4.6+ di Adobe Commerce/Magento Open Source ancora una volta, perché altrimenti non potrai selezionare le [!DNL Metric System/SI] misurazioni di **chilogrammi** e **centimetri** nei metodi di spedizione [!DNL UPS] **[!DNL Admin configuration]**. Queste nuove patch sono compatibili con le patch rilasciate in precedenza. Questo problema verrà risolto definitivamente nell&#39;ambito della prossima versione di Adobe Commerce 2.4.7-p1 pianificata per il **11 giugno 2024**.

>[!NOTE]
>
>Se hai caricato una delle tre patch di questo articolo prima del **10 ottobre 2023**, devi riapplicare una di queste patch ora pubblicata in questo articolo per la tua versione 2.4.4+/2.4.5+/2.4.6+ di Adobe Commerce/Magento Open Source ancora una volta, altrimenti non potrai selezionare e configurare specifici [!DNL UPS] metodi di spedizione in **[!DNL Admin configuration]** e dovrai avere tutti abilitati. Queste nuove patch sono compatibili con le patch rilasciate in precedenza.

Questo articolo fornisce una patch per risolvere i problemi relativi alla migrazione dell&#39;integrazione del metodo di spedizione [!DNL United Parcel Service (UPS)] da [!DNL SOAP] a [!DNL RESTful API] per Adobe Commerce 2.4.4 - 2.4.6-pX.

In base agli ultimi aggiornamenti al modello di sicurezza [!DNL UPS API], [!DNL UPS] ha implementato un modello di sicurezza [!DNL OAuth 2.0] per tutti i [!DNL APIs] (ulteriori dettagli disponibili nella [[!DNL UPS] Guida alla migrazione della chiave di accesso al portale per sviluppatori](https://developer.ups.com/oauth-developer-guide?loc=en_US&amp;sp_rid=NTA5MzQ1OTE2NjEyS0&amp;sp_mid=72989914)) per migliorare la sicurezza complessiva al fine di ridurre le frodi e fornire funzionalità [!DNL API] avanzate.

Questa modifica influisce sull&#39;implementazione corrente del metodo di spedizione [!DNL UPS] in Adobe Commerce e richiede la correzione dell&#39;implementazione corrente e la migrazione da [!DNL SOAP API] a [!DNL RESTful API] per supportare i protocolli di autenticazione [!DNL OAuth 2.0].

**A partire da giugno 2024**, i commercianti Adobe Commerce non saranno in grado di negoziare con l&#39;integrazione [!DNL UPS] corrente, pertanto stiamo rilasciando questo hotfix, che consente ai commercianti Adobe Commerce 2.4.4+/2.4.5+/2.4.6+ di migrare all&#39;ultima [!DNL UPS REST APIs].

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

[!DNL UPS] ha rilasciato un aggiornamento di sicurezza [per il suo [!DNL API]](https://developer.ups.com/oauth-developer-guide?loc=en_US&amp;sp_rid=NTA5MzQ1OTE2NjEyS0&amp;sp_mid=72989914).

Se si dispone dell&#39;Unione europea (altre origini potrebbero riscontrare lo stesso problema) come origine della spedizione, si verificherà un errore nella richiesta [!DNL UPS REST]:
&quot;*Una spedizione non può avere come unità di misura KGS/IN, LBS/CM o OZS/CM.*&quot;

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

Decomprimi il file e vedi [Come applicare una patch del compositore fornita dall&#39;Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) nella Knowledge Base di supporto per le istruzioni.

## Come stabilire se i cerotti sono stati applicati

Considerando che non è possibile verificare facilmente se il problema è stato corretto, è possibile verificare se la patch è stata applicata correttamente. In questo modo viene utilizzata (esempio: *AC-9363*) come patch da controllare.

<u>A tale scopo, procedere come segue</u>:

1. [Installa  [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. Esegui il comando:

   ```bash
   vendor/bin/magento-patches -n status |grep "9363|Status"
   ```

1. Dovresti vedere un output simile a questo, dove AC-9363 restituisce lo stato *Applicato*:

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/AC-9363_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```
