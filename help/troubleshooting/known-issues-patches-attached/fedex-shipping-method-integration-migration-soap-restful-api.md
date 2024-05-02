---
title: '''[!DNL FedEx] migrazione dell’integrazione del metodo di spedizione da SOAP all’API RESTful'
promoted: true
description: Applicare una patch per gestire [!DNL FedEx] migrazione dell’integrazione del metodo di spedizione dall’API SOAP all’API RESTful per Adobe Commerce 2.4.4-p4 - 2.4.6-pX.
feature: Shipping/Delivery
role: Developer
exl-id: 7e11a171-6924-41d0-a5c7-7b794d0da84c
source-git-commit: 7c468583883789a6bc6e41d1a787a356ea3205c4
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# [!DNL FedEx] migrazione dell’integrazione del metodo di spedizione da SOAP all’API RESTful

Questo articolo fornisce una patch per risolvere i problemi relativi a [!DNL FedEx] migrazione dell’integrazione del metodo di spedizione dall’API SOAP all’API RESTful per Adobe Commerce 2.4.4-p4 - 2.4.6-pX.

[!DNL FedEx Web Services] tracking, convalida degli indirizzi e convalida dei codici postali I linguaggi di definizione dei servizi web (WSDLS) verranno ritirati il 15 maggio 2024. Basato su SOAP [!DNL FedEx Web Services] è in fase di sviluppo ed è stato sostituito con [!DNL FedEx] API RESTFUL. Per ulteriori informazioni, consulta [[!DNL FedEx Web Services]](https://www.fedex.com/en-us/developer/web-services.html).

Questo cambiamento influisce sulla nostra attuale [!DNL FedEx] implementazione dell’integrazione del metodo di spedizione in Adobe Commerce, richiede la correzione dell’implementazione corrente e la migrazione dalle API SOAP obsolete all’ultima versione [!DNL FedEx] API RESTFUL.

A partire dal 15 maggio 2024, i clienti di Adobe Commerce non potranno utilizzare i nostri [!DNL FedEx] per l’integrazione del metodo di spedizione, Adobe sta rilasciando questo hotfix che consente ai clienti Adobe Commerce 2.4.4+ di utilizzare la versione più recente [!DNL FedEx] API RESTFUL anziché SOAP obsolete.


## Prodotti e versioni interessati

Adobe Commerce su infrastruttura cloud e on-premise e Magento Open Source:

* 2.4.4-p4
* 2.4.5.
* 2,4,5-pX
* 2.4.6.
* 2,4,6-pX

## Causa

Il [!DNL FedEx] hanno dichiarato obsolete le API basate su SOAP e le hanno sostituite con quelle RESTful. Fai riferimento a [[!DNL FedEx Web Services]](https://www.fedex.com/en-us/developer/web-services.html).

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
