---
title: "ACSD-59036: si verifica un’eccezione durante il caricamento dei prezzi dei prodotti con limiti inferiore e superiore impostati su $0"
description: Applica la patch ACSD-59036 per risolvere il problema Adobe Commerce in cui si verifica un’eccezione durante il caricamento dei prezzi dei prodotti con limiti inferiori e superiori impostati su *$0*.
feature: Categories, Products, Storefront, Search
role: Admin, Developer
source-git-commit: d711fb8ff8876a4a514daade6d7df4d7cf7e3593
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---


# ACSD-59036: si verifica un&#39;eccezione durante il caricamento dei prezzi dei prodotti con limiti inferiore e superiore impostati su *$0*

La patch ACSD-59036 risolve il problema relativo a un&#39;eccezione durante il caricamento dei prezzi dei prodotti con limiti inferiore e superiore impostati su *$0*. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50. L’ID della patch è ACSD-59036. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.7

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.7 - 2.4.7-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Eccezione durante il caricamento dei prezzi dei prodotti con limiti inferiore e superiore impostati su *$0*.

Il problema si verifica perché l’algoritmo non tiene conto dei valori NULL durante il caricamento della query con intervalli di prezzi. Per risolvere questo problema, è possibile verificare se entrambi gli intervalli inferiore e superiore sono NULL e, in caso affermativo, assegnare un valore di *0* per entrambi i limiti. Questo dovrebbe evitare la generazione di errori.

<u>Passaggi da riprodurre</u>:

1. Crea *13* prodotti semplici.
1. Assegna tutti i prodotti *13* a una categoria.
1. Impostare il prezzo di un prodotto su *$1322.94*.
1. Impostare il prezzo di tutti gli altri prodotti su *$0*.
1. Configura [!DNL OpenSearch] come motore di ricerca.
1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Storefront]** e imposta il conteggio di **[!UICONTROL PLP]** su *16*.
1. Imposta **[!UICONTROL Price Navigation Step Calculation]** su *Automatico (equalizza conteggi prodotti)*.
1. Esegui reindicizzazione completa.
1. Aprire la pagina *[!UICONTROL Category]*.

<u>Risultati previsti</u>:

Nella pagina *[!UICONTROL Category]* vengono visualizzati tutti i prodotti.

<u>Risultati effettivi</u>:

Si verifica un errore:

```JSON
report.CRITICAL: OpenSearch\Common\Exceptions\BadRequest400Exception: {"error":{"root_cause":[{"type":"x_content_parse_exception","reason":"[1:193] [bool] failed to parse field [must]"}],"type":"x_content_parse_exception","reason":"[1:193] [bool] failed to parse field [filter]","caused_by":{"type":"x_content_parse_exception","reason":"[1:193] [bool] failed to parse field [must]","caused_by":{"type":"illegal_argument_exception","reason":"field name is null or empty"}}},"status":400} in /vendor/opensearch-project/opensearch-php/src/OpenSearch/Connections/Connection.php:664
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
