---
title: Migrazione dell'integrazione del metodo di spedizione [!DNL FedEx] da SOAP all'API RESTful
promoted: true
description: Applica una patch per gestire la migrazione dell'integrazione del metodo di spedizione  [!DNL FedEx]  dall'SOAP all'API RESTful per Adobe Commerce 2.4.4-p4 - 2.4.6-pX.
feature: Shipping/Delivery
role: Developer
exl-id: 7e11a171-6924-41d0-a5c7-7b794d0da84c
source-git-commit: 7a54e992e365238ec7c764225a31cd3b6b8ad019
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---

# Migrazione dell&#39;integrazione del metodo di spedizione [!DNL FedEx] da SOAP all&#39;API RESTful

>[!WARNING]
>
>Utilizzare la patch ACSD-61622 di [!DNL Quality Patches Tool] (QPT) versione 1.1.57 invece della patch fornita in precedenza. La nuova patch è compatibile con le versioni di Adobe Commerce (tutti i metodi di distribuzione) 2.4.6-p1 - 2.4.6-p8. Potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool].
>
>Per ulteriori informazioni, consulta l&#39;[articolo sulla patch ACSD-61622](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-57/acsd-61622-fedex-account-specific-rates-missing-from-response) nella guida degli strumenti di Adobe Commerce.

>[!WARNING]
>
>Prima di installare la nuova patch, è necessario disinstallare la patch precedente fornita in questo articolo. Per istruzioni sulla disinstallazione delle patch, consulta [Ripristinare una patch personalizzata](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches#revert-a-custom-patch) nella guida utente.


Questo articolo fornisce una patch per risolvere i problemi relativi alla migrazione dell&#39;integrazione del metodo di spedizione [!DNL FedEx] dall&#39;SOAP all&#39;API RESTful per Adobe Commerce 2.4.4-p4 - 2.4.6-pX.

Il tracciamento di [!DNL FedEx Web Services], la convalida degli indirizzi e la convalida dei codici postali WSDLS (Web Services Definition Languages) sono stati ritirati il 15 maggio 2024. [!DNL FedEx Web Services] basato su SOAP è in fase di sviluppo ed è stato sostituito con [!DNL FedEx] API RESTFUL. Per ulteriori informazioni, consultare [[!DNL FedEx Web Services]](https://www.fedex.com/en-us/developer/web-services.html).

Questa modifica influisce sull&#39;implementazione corrente del metodo di spedizione [!DNL FedEx] in Adobe Commerce e richiede la correzione dell&#39;implementazione corrente e la migrazione dalle API SOAP obsolete alle API RESTFUL [!DNL FedEx] più recenti.

A partire dal 15 maggio 2024, i clienti di Adobe Commerce non saranno in grado di utilizzare l&#39;attuale integrazione del metodo di spedizione [!DNL FedEx]. Pertanto, Adobe sta rilasciando questo hotfix che consente ai clienti Adobe Commerce 2.4.4+ di utilizzare le API RESTFUL [!DNL FedEx] più recenti invece di quelle SOAP obsolete.


## Prodotti e versioni interessati

Adobe Commerce su infrastruttura cloud e on-premise e Magento Open Source:

* 2.4.4-p4
* 2.4.5.
* 2,4,5-pX
* 2.4.6.
* 2,4,6-pX

## Causa

[!DNL FedEx] ha dichiarato obsolete le API basate su SOAP sostituendole con quelle RESTful. Fare riferimento a [[!DNL FedEx Web Services]](https://www.fedex.com/en-us/developer/web-services.html).

## Soluzione

Utilizza le seguenti patch allegate, a seconda della versione di Adobe Commerce/Magento Open Source in uso:

Per risolvere il problema nelle versioni 2.4.4+, 2.4.5+ e 2.4.6+, è necessario applicare la patch corrispondente alla versione di Adobe Commerce/Magento Open Source in uso.

## Patch

Utilizza le seguenti patch allegate, a seconda della versione di Adobe Commerce/Magento Open Source in uso:

### Per le versioni 2.4.4-p4:

* [FedexPatch-Composer-245p5-244p6develop.patch.zip](assets/FedexPatch-Composer-245p5-244p6develop.patch.zip)

### Per le versioni 2.4.5, 2.4.5-pX:

* [FedexPatch-Composer-245p5-244p6develop.patch.zip](assets/FedexPatch-Composer-245p5-244p6develop.patch.zip)


### Per le versioni 2.4.6, 2.4.6-pX:


* [FedexPatch-Composer-246p3develop.patch.zip](assets/FedexPatch-Composer-246p3develop.patch.zip)


## Come applicare il cerotto

Decomprimi il file e vedi [Come applicare una patch del compositore fornita da Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) nella Knowledge Base di supporto per le istruzioni.

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
