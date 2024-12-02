---
title: 'ACSD-56415: prestazioni di [!UICONTROL Partial Price Indexing] rallentate a causa della query "DELETE"'
description: Applica la patch ACSD-56415 per risolvere il problema di Adobe Commerce in cui le prestazioni di [!UICONTROL Partial Price Indexing] sono rallentate a causa di una query "DELETE" quando il database ha molti dati di prezzo parziali da indicizzare.
feature: Catalog Service
role: Admin, Developer
exl-id: 0b099570-9f27-4ae2-9384-6b69ea50bd98
source-git-commit: 8b6bf1cdada7edb0cdb0bb3e90ed15ee8cebf77e
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-56415: le prestazioni di [!UICONTROL Partial Price Indexing] sono rallentate a causa della query `DELETE`

La patch ACSD-56415 risolve il problema che rallenta le prestazioni di [!UICONTROL Partial Price Indexing] a causa di una query `DELETE` quando il database ha un indice parziale dei dati di prezzo. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45. L’ID della patch è ACSD-56023. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le prestazioni di [!UICONTROL Partial Price Indexing] sono rallentate a causa di una query `DELETE` quando il database presenta molti indici di dati di prezzo parziali.

<u>Passaggi da riprodurre</u>:

1. Crea *300000 prodotti* e *10 siti Web* utilizzando il profilo di prestazioni elevato.
1. Accedi al pannello di amministrazione.
1. Crea *10 gruppi di clienti*.
1. Eseguire la query seguente per aggiungere prodotti alla tabella `_cl`:

   ``
    insert into catalog_product_price_cl (entity_id) select entity_id from catalog_product_entity
 ``

1. Esegui il comando seguente per attivare il processo di indicizzazione parziale dei prezzi:

   ``
    bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
 ``

<u>Risultati previsti</u>:

Il DELETE query SQL `main_table` FROM `catalog_product_index_price` viene eseguito rapidamente.

<u>Risultati effettivi</u>:

Il DELETE query SQL `main_table` FROM `catalog_product_index_price` viene eseguito molto lentamente.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
