---
title: '[!DNL USPS] hotfix di supporto per il metodo di spedizione Ground Advantage per AC-9182'
promoted: true
description: 'Applicare una patch per risolvere il problema AC-9182 del metodo di spedizione Ground Advantage per Adobe Commerce 2.4.4 - 2.4.6-p2. [!DNL USPS] '
feature: Shipping/Delivery
role: Developer
exl-id: b6871d19-3d02-4026-82e6-3545f4ab7159
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# [!DNL USPS] hotfix di supporto per il metodo di spedizione Ground Advantage per AC-9182

Questo articolo fornisce una patch per risolvere il problema AC-9182 per il nuovo metodo di spedizione **[!DNL USPS]Ground Advantage** in Adobe Commerce 2.4.4 - 2.4.6-p2.

Il 9 luglio 2023, il servizio postale degli Stati Uniti ([!DNL USPS]) ha rilasciato un nuovo metodo di spedizione, [[!DNL USPS] Ground Advantage](https://www.usps.com/ship/ground-advantage.htm).

Questo nuovo metodo di spedizione sta sostituendo i tre principali metodi di spedizione attuali:

* [!DNL USPS] vendita al dettaglio
* [!DNL USPS] servizio pacchetto di prima classe
* [!DNL USPS] terreno di selezione pacchetto

[[!DNL USPS] ha annunciato](https://faq.usps.com/s/article/USPS-Ground-Advantage#how_it_works) che a partire dal 30 settembre 2023 questi tre metodi di spedizione verranno interrotti e tutti i clienti dovranno utilizzare il nuovo metodo **[!DNL USPS]Ground Advantage**.

Pertanto, dopo il 30 settembre 2023, tutti i commercianti Adobe Commerce che utilizzano il metodo di spedizione USPS non saranno più in grado di ottenere tariffe di spedizione da [!DNL USPS] utilizzando questi tre metodi di spedizione legacy.

Questo problema verrà risolto nell’ambito delle prossime versioni delle patch di sola sicurezza a ottobre 2023, nelle versioni 2.4.6-p3, 2.4.5-p5 e 2.4.4-p6.

## Prodotti e versioni interessati

Adobe Commerce su infrastruttura cloud e on-premise e Magento Open Source:

* 2.4.4.
* 2.4.4-p1
* 2.4.4-p2
* 2.4.4-p3
* 2.4.4-p4
* 2.4.4-p5
* 2.4.5.
* 2,4,5-p1
* 2.4.5-p2
* 2.4.5-p3
* 2,4,5-p4
* 2.4.6.
* 2.4.6-p1
* 2.4.6-p2

## Causa

[!DNL USPS] ha effettuato un aggiornamento di [!DNL API].

## Soluzione

Per risolvere il problema nelle versioni 2.4.4, 2.4.5 e 2.4.6, è necessario applicare la patch AC-9182 di seguito.

## Patch

La patch è allegata a questo articolo. Per scaricarlo, fai clic sul seguente collegamento:

[AC-9182_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.zip](assets/AC-9182_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.zip)

## Come applicare il cerotto

Decomprimi il file e vedi [Come applicare una patch del compositore fornita da Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html?lang=it) nella Knowledge Base di supporto per le istruzioni.

## Come stabilire se i cerotti sono stati applicati

Considerando che non è possibile verificare facilmente se il problema è stato corretto, è possibile verificare se la patch AC-9182 è stata applicata correttamente.

<u>A tale scopo, procedere come segue</u>:

1. [Installa  [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it).
1. Esegui il comando:

   ```bash
   vendor/bin/magento-patches -n status |grep "9182|Status"
   ```

1. Dovresti vedere un output simile a questo, dove AC-9182 restituisce lo stato *Applicato*:

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/AC-9182_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```
