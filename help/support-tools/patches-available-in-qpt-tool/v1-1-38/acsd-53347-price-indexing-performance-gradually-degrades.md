---
title: 'ACSD-53347: le prestazioni di indicizzazione dei prezzi si riducono gradualmente nel tempo'
description: Applica la patch ACSD-53347 per risolvere il problema Adobe Commerce, in cui le prestazioni si riducono gradualmente quando si indicizzano i prezzi di un catalogo di prodotti di grandi dimensioni.
feature: Price Indexer
role: Admin
exl-id: 28795673-54b0-4282-bd43-344401cbe140
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# ACSD-53347: le prestazioni di indicizzazione dei prezzi si riducono gradualmente nel tempo

La patch ACSD-53347 risolve il problema del graduale peggioramento delle prestazioni quando si indicizzano i prezzi di un catalogo di prodotti di grandi dimensioni. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.38. L’ID della patch è ACSD-53347. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando si indicizzano i prezzi di un catalogo di prodotti di grandi dimensioni, le prestazioni delle query eseguite durante il processo di indicizzazione si riducono gradualmente.

<u>Passaggi da riprodurre</u>:

1. Crea un catalogo semplice di grandi dimensioni e assegna opzioni personalizzate a questi prodotti (le opzioni personalizzate utilizzano una tabella temporanea durante l’indicizzazione).
1. Crea almeno 200 o più gruppi di clienti per aumentare la visibilità del problema.
1. Crea dieci o più siti Web e assegna tutti i prodotti a ciascuno di essi.
1. I prodotti importati sono quasi identici e si differenziano solo per SKU e nome.
1. Abilita **[!UICONTROL DB Logging]**.
1. Eseguire il comando `bin/magento index:reindex catalog_product_price`.
1. Controllare *DELETE FROM`catalog_product_index_price_opt_agr_temp`* in `db.log`.

<u>Risultati previsti</u>:

L&#39;esecuzione delle *query DB* viene eseguita in modo efficiente.

<u>Risultati effettivi</u>:

Le prestazioni delle *query DB* nelle tabelle temporanee diventano lente nel tempo, pertanto il completamento dell&#39;indicizzazione dei prezzi richiede molto tempo.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
