---
title: '"ACSD-56415: Prestazioni di [!UICONTROL Partial Price Indexing] rallentato a causa di una query "DELETE"'
description: Applicare la patch ACSD-56415 per risolvere il problema Adobe Commerce in cui le prestazioni del [!UICONTROL Partial Price Indexing] è rallentato a causa di una query "DELETE" quando il database ha molti dati parziali sul prezzo da indicizzare.
feature: Catalog Service
role: Admin, Developer
exl-id: 0b099570-9f27-4ae2-9384-6b69ea50bd98
source-git-commit: fe6269ac042326a85a2cab5ccf834ac3eff1c166
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-56415: Prestazioni di [!UICONTROL Partial Price Indexing] è rallentato a causa `DELETE` query

La patch ACSD-56415 risolve il problema relativo alle prestazioni [!UICONTROL Partial Price Indexing] è rallentato a causa di un `DELETE` eseguire una query quando nel database è presente un indice dei dati prezzi parziale elevato. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45. L’ID della patch è ACSD-56023. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le prestazioni di [!UICONTROL Partial Price Indexing] è rallentato a causa di un `DELETE` eseguire una query quando nel database è presente un indice dei dati prezzi parziale elevato.

<u>Passaggi da riprodurre</u>:

1. Crea *300000 prodotti* e *10 siti web* utilizzando il profilo di prestazioni elevato.
1. Accedi al pannello di amministrazione.
1. Crea *10 gruppi di clienti*.
1. Esegui la query seguente per aggiungere prodotti al `_cl` tabella:

   ``
    insert into catalog_product_price_cl (entity_id) select entity_id from catalog_product_entity
 ``

1. Esegui il comando seguente per attivare il processo di indicizzazione parziale dei prezzi:

   ``
    bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
 ``

<u>Risultati previsti</u>:

Query DELETE SQL `main_table` DA `catalog_product_index_price` viene eseguito rapidamente.

<u>Risultati effettivi</u>:

Query DELETE SQL `main_table` DA `catalog_product_index_price` viene eseguito molto lentamente.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
