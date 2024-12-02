---
title: 'ACSD-53098: i prodotti nel catalogo condiviso non si riflettono sul front-end'
description: Applica la patch ACSD-53098 per risolvere il problema Adobe Commerce per cui i prodotti assegnati a un catalogo condiviso non si riflettono sul front-end durante l’esecuzione di un indice parziale.
feature: B2B, Catalog Management, Categories, Products
role: Admin, Developer
exl-id: 19c66a3a-04b2-48ee-aff3-ad2b592ff876
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-53098: i prodotti nel catalogo condiviso non si riflettono sul front-end

La patch ACSD-53098 risolve il problema per cui i prodotti assegnati a un catalogo condiviso non si riflettono sul front-end durante l’esecuzione di un indice parziale. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.38. L’ID della patch è ACSD-53098. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.3-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I prodotti assegnati a un catalogo condiviso tramite API non vengono visualizzati sul front-end dopo che l’indicizzatore parziale esegue il processo cron, seguito dal cron del consumatore.

<u>Passaggi da riprodurre</u>:

1. Imposta [!DNL RabbitMQ] come servizio di coda.
1. Passa alla modalità **[!UICONTROL Update on Schedule]**.
1. Crea un catalogo condiviso e assegnalo a un’azienda.
1. Crea un prodotto semplice e assegnalo a una categoria. Esegui la reindicizzazione parziale:

   `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1`

1. Utilizza la seguente richiesta API per assegnare il prodotto creato al catalogo condiviso.

   ```
   pub/rest/all/V1/sharedCatalog/<id>/assignProducts
   {
       "products":[{
           "sku": "24-MB06"
           }
       ]
   }
   ```

1. Esegui la seguente cron per cancellare le code ed eseguire la reindicizzazione parziale:

   `bin/magento cron:run --group=consumers`

   `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1`

1. Accedi al front-end come utente dell’azienda.
1. Consultate la pagina delle categorie front-end.

<u>Risultati previsti</u>:

I prodotti appena assegnati vengono visualizzati sul front-end.

<u>Risultati effettivi</u>:

I prodotti appena assegnati non vengono visualizzati sul front-end.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
