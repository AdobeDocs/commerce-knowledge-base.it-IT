---
title: 'ACSD-46617: pulsante **[!UICONTROL Continue to Checkout]** disattivato quando il subtotale è maggiore dell''importo minimo dell''ordine configurato'
description: Applicare la patch ACSD-46617 per risolvere il problema di Adobe Commerce in cui il pulsante **[!UICONTROL Continue to Checkout]** è disattivato anche se il subtotale è maggiore dell'importo dell'ordine minimo configurato.
exl-id: 42fe02bd-f48b-4c6d-8643-ea2c1aa98c94
feature: Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-46617: pulsante &quot;[!UICONTROL Continue to Checkout]&quot; disabilitato quando il subtotale è maggiore di &quot;[!UICONTROL Minimum Order Amount]&quot;

Questa patch ACSD-46617 risolve il problema in cui il pulsante **[!UICONTROL Continue to Checkout]** è disattivato anche se il subtotale è maggiore dell&#39;importo dell&#39;ordine minimo configurato. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24. L’ID della patch è ACSD-46617. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il pulsante **[!UICONTROL Continue to Checkout]** è disattivato anche se il subtotale è maggiore dell&#39;importo minimo dell&#39;ordine configurato.

<u>Passaggi da riprodurre</u>:

1. Vai a Adobe Commerce Admin > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Minimum Order Amount]** e imposta quanto segue:
   * [!UICONTROL Enable]: *[!UICONTROL Yes]*
   * 
     [!UICONTROL Minimum Amount]: *2*

1. Crea un [!UICONTROL Cart Price Rule].
   * [!UICONTROL Coupon Code]: *[!UICONTROL TEST (optional)]*
   * [!UICONTROL Conditions]: *[!UICONTROL Keep empty]*
   * [!UICONTROL Actions]:
      * [!UICONTROL Apply]: *[!UICONTROL Percent of product price discount]*
      * 
        [!UICONTROL Discount Amount]: *92*
      * [!UICONTROL Apply to Shipping Amount]: *[!UICONTROL Yes]*
1. Crea un prodotto al prezzo di 25 $.
1. Aggiungi il prodotto al carrello.
1. Vai al carrello, seleziona il metodo $5 **[!UICONTROL Flat Rate shipping]** e applica il codice del coupon.
1. Passare al checkout, completare la spedizione e passare alla sezione **[!UICONTROL Paytment]**.
1. Torna al carrello.

<u>Risultati previsti</u>:

Non c&#39;è alcun errore relativo all&#39;importo minimo dell&#39;ordine in quanto il totale complessivo di $ 2,4 è maggiore dell&#39;importo richiesto di $ 2.

<u>Risultati effettivi</u>:

* Si è verificato un errore relativo all’importo minimo dell’ordine anche quando il totale complessivo di 2,4 $ è maggiore dell’importo minimo dell’ordine di 2 $.
* Il pulsante **[!UICONTROL Continue to Checkout]** è disattivato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
