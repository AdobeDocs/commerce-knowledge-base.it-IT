---
title: 'ACSD-51846: errore interno perché  [!DNL REST API] i livelli di payload non sono convalidati'
description: Applica la patch ACSD-51846 per risolvere il problema Adobe Commerce in cui si verifica un "Errore interno" poiché non tutti i livelli del payload  [!DNL REST API]  sono convalidati.
feature: REST
role: Developer
exl-id: 17ce5cca-063d-439c-9390-f5e2bf5b696b
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-51846: errore interno perché i livelli di payload [!DNL REST API] non sono convalidati

La patch ACSD-51846 risolve il problema relativo a un &quot;Errore interno&quot;, in quanto non tutti i livelli del payload [!DNL REST API] sono convalidati. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.36. L’ID della patch è ACSD-51846. Il problema è stato risolto in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p2 - 2.4.5-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Si è verificato un &quot;errore interno&quot; poiché tutti i livelli del payload [!DNL REST API] non sono convalidati.

<u>Passaggi da riprodurre</u>:

1. Aggiungi un prodotto al carrello del cliente.
1. Invia la richiesta [!DNL REST API] a `rest/V1/carts/mine/estimate-shipping-methods` utilizzando un attributo &quot;_street non corretto._&quot; con un punto alla fine.

```
 {
    "address": {
         "street.": [
             "\uc11c\uc6b8 \uac15\ubd81\uad6c \ud55c\ucc9c\ub85c166\uae38 2 (-\uc11c\uc6b8 \uac15\ubd81\uad6c \uc218\uc720\ub3d9 269-36)"
         ],
         "city": "pune",
         "region": null,
         "country_id": "IN",
         "postcode": "411015",
         "customer_id": "2",
         "firstname": "test",
         "lastname": "test",
         "middlename": null,
         "prefix": null,
         "suffix": null,
         "vat_id": null,
         "company": null,
         "telephone": "00000000000",
         "fax": null,
         "custom_attributes": []
     }
 }
```

<u>Risultati previsti</u>:

L&#39;endpoint deve convalidare il parametro e restituire `400 status code` con un messaggio di errore specifico. Esempio:

```
report.CRITICAL: LogicException: Property "Street." does not have accessor method "getStreet." in class "Magento\Quote\Api\Data\AddressInterface". in vendor/magento/framework/Reflection/NameFinder.php:103
```

<u>Risultati effettivi</u>:

L&#39;endpoint non convalida il parametro errato e restituisce l&#39;errore `500 status code`.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
