---
title: 'ACSD-53750: errore "Connessione interrotta o chiusa" durante la reindicizzazione di catalog_product_price multithread'
description: Applicate la patch ACSD-53750 per risolvere il problema Adobe Commerce che si verifica in caso di errore *Broken pipe o closed connection* durante la reindicizzazione multi-threaded catalog_product_price.
feature: Products
role: Admin, Developer
exl-id: afb30384-74e7-4857-9aff-8e99f5abc309
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-53750 *Tubo rotto o connessione chiusa* errore durante multithreading `catalog_product_price` reindicizzare

La patch ACSD-53750 risolve il problema in cui *Tubo rotto o connessione chiusa* si verifica un errore durante il multithreading `catalog_product_price` reindicizzare. Questa patch è disponibile quando [!DNL Quality Patches Tool (QPT)] 1.1.37. L’ID della patch è ACSD-53750. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

*Tubo rotto o connessione chiusa* si verifica un errore durante il multithreading `catalog_product_price` reindicizzare.

<u>Passaggi da riprodurre</u>:

1. Configurare RabbitMq.
1. Genera dati di esempio utilizzando il `small.xml` file.
1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Inventory Indexer Setting]** e imposta **[!UICONTROL Stock/Source reindex strategy]** = **[!UICONTROL Asynchronous]**.
1. Imposta la modalità dimensione per gli indici che la supportano. Ad esempio: `catalog_product_price_website_and_customer_group` o `customer_group`.

   ```
   bin/magento indexer:set-dimensions-mode catalog_product_price customer_group
   ```

1. Esegui reimpostazione degli indicizzatori per `catalog_product_price`.

   ```
   bin/magento indexer:reset catalog_product_price
   ```

1. Eseguire l&#39;indicizzatore per l&#39;indicizzatore di reimpostazione utilizzando più thread.

   ```
   MAGE_INDEXER_THREADS_COUNT=10 bin/magento indexer:reindex catalog_product_price
   ```

<u>Risultati previsti</u>:

Nessun errore.

<u>Risultati effettivi</u>:

Il seguente errore è causato da una connessione AMQP: *Tubo rotto o connessione chiusa*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
