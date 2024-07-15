---
title: "ACSD-53925: impossibile salvare il blocco CMS con [!UICONTROL Product Carousel]"
description: Applica la patch ACSD-53925 per risolvere il problema di Adobe Commerce, in cui l’amministratore non è in grado di salvare un blocco CMS con Product Carousel quando la modalità dimensioni per "catalog_product_price" è impostata su sito web.
feature: CMS, Page Builder, Price Indexer, Products
role: Admin, Developer
exl-id: 6ef6d8ff-4ebb-4adb-9fb7-0d4a81a25f50
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# ACSD-53925: impossibile salvare il blocco CMS con *[!UICONTROL Product Carousel]*

La patch ACSD-53925 risolve il problema che impediva all&#39;amministratore di salvare un blocco CMS con *[!UICONTROL Product Carousel]* quando la modalità dimensioni per `catalog_product_price` è impostata su sito Web. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.43. L’ID della patch è ACSD-53925. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;amministratore non è in grado di salvare un blocco CMS con *[!UICONTROL Product Carousel]* quando la modalità dimensioni per `catalog_product_price` è impostata su Sito Web.

<u>Passaggi da riprodurre</u>:

1. Crea due prodotti semplici:
   * simple1 - $10
   * simple2 - $20
1. Creare un prodotto bundle &#39;*bundle1-dyn*&#39; con due opzioni basate su SKU di prodotto semplici.
1. Imposta modalità dimensioni per l&#39;indicizzatore prezzo prodotto:

   `bin/magento indexer:set-dimensions-mode catalog_product_price website`

1. Vai a **[!UICONTROL Content]** > **[!UICONTROL Blocks]** e crea un nuovo blocco CMS.
1. Modifica il contenuto utilizzando [!DNL Page Builder]:
   * Aggiungi un elemento *[!UICONTROL Row]*
   * Aggiungi un elemento *[!UICONTROL Products]*
   * Seleziona *[!UICONTROL Product Carousel]*
   * Immetti SKU prodotto - *bundle1-dyn*
1. Salva il blocco CMS.

<u>Risultati previsti</u>:

L’utente può aggiungere un carosello di prodotto senza errori.

<u>Risultati effettivi</u>:

* Messaggio generato nell&#39;interfaccia utente: *Si è verificato un errore durante la generazione del contenuto*
* `var/log/exception.log` contiene il seguente errore:

  ```
  [2023-08-18T20:58:14.533374+00:00] report.CRITICAL: PDOException: SQLSTATE[42S02]: Base table or view not found: 1146 Table 'username_dev.catalog_product_index_price_ws0' doesn't exist in /test/lib/internal/Magento/Framework/DB/Statement/Pdo/Mysql.php:90
  ```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
