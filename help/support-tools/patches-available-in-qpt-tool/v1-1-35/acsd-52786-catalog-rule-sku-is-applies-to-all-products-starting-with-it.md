---
title: 'ACSD-52786: la regola catalogo *[!UICONTROL SKU is]* si applica a tutti i prodotti che iniziano con lo SKU'
description: Applica la patch ACSD-52786 per risolvere il problema Adobe Commerce, in cui la condizione della regola catalogo *[!UICONTROL SKU is]* si applica a tutti i prodotti che iniziano con lo SKU specificato.
feature: Price Rules
role: Admin
exl-id: af373b6c-5944-412b-a544-cc6fc3f209d3
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# ACSD-52786: la regola catalogo &quot;*[!UICONTROL SKU is]*&quot; si applica a tutti i prodotti che iniziano con lo SKU

La patch ACSD-52786 risolve il problema per cui la condizione della regola catalogo *[!UICONTROL SKU is]* si applica a tutti i prodotti che iniziano con lo SKU specificato. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.35. L’ID della patch è ACSD-52786. Il problema è stato risolto in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.5-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La condizione della regola catalogo *[!UICONTROL SKU is]* si applica a tutti i prodotti che iniziano con lo SKU specificato.

<u>Passaggi da riprodurre</u>:

1. Creare due prodotti, uno con SKU &quot;24&quot; e un altro con SKU &quot;24-MB01&quot;.
1. Passa a **[!UICONTROL Marketing]** > **[!UICONTROL Catalog Price Rule]** > **[!UICONTROL Add New Rule]**.
1. Applica la seguente condizione:
   * *[!UICONTROL If **&#x200B; TUTTE &#x200B;** di queste condizioni sono **&#x200B; TRUE &#x200B;**]*: *[!UICONTROL SKU is 24]*
1. Imposta qualsiasi importo di sconto nelle azioni.
1. Fare clic su **[!UICONTROL Save and Apply]**.
1. Svuota cache.
1. Vai alla vetrina e controlla il prezzo di 24-MB01.

<u>Risultati previsti</u>:

La regola del catalogo viene applicata solo a un singolo prodotto con SKU uguale a 24.

<u>Risultati effettivi</u>:

La condizione della regola catalogo *[!UICONTROL SKU is]* si applica a tutti i prodotti che iniziano con lo SKU specificato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
