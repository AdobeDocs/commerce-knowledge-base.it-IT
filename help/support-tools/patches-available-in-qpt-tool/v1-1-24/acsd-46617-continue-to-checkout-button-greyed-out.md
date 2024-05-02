---
title: "ACSD-46617: **[!UICONTROL Continue to Checkout]Il pulsante ** è disattivato quando il subtotale è superiore all’importo minimo dell’ordine configurato"
description: Applica la patch ACSD-46617 per risolvere il problema di Adobe Commerce in cui il **[!UICONTROL Continue to Checkout]** pulsante è disattivato anche se il subtotale è maggiore dell’importo minimo dell’ordine configurato.
exl-id: 42fe02bd-f48b-4c6d-8643-ea2c1aa98c94
feature: Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-46617: &quot;[!UICONTROL Continue to Checkout]&quot;Il pulsante è disattivato quando il subtotale è maggiore di&quot;[!UICONTROL Minimum Order Amount]&quot;

Questa patch ACSD-46617 risolve il problema in cui **[!UICONTROL Continue to Checkout]** il pulsante è disattivato anche se il subtotale è maggiore dell’importo minimo dell’ordine configurato. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24. L’ID della patch è ACSD-46617. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il **[!UICONTROL Continue to Checkout]** il pulsante è disattivato anche se il subtotale è maggiore dell’importo minimo dell’ordine configurato.

<u>Passaggi da riprodurre</u>:

1. Vai a Amministrazione di Adobe Commerce > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Minimum Order Amount]** e impostare quanto segue:
   * [!UICONTROL Enable]: *[!UICONTROL Yes]*
   * 
     [!UICONTROL Minimum Amount]: *2*

1. Creare un [!UICONTROL Cart Price Rule].
   * [!UICONTROL Coupon Code]: *[!UICONTROL TEST (optional)]*
   * [!UICONTROL Conditions]: *[!UICONTROL Keep empty]*
   * [!UICONTROL Actions]:
      * [!UICONTROL Apply]: *[!UICONTROL Percent of product price discount]*
      * 
        [!UICONTROL Discount Amount]: *92*
      * [!UICONTROL Apply to Shipping Amount]: *[!UICONTROL Yes]*
1. Crea un prodotto al prezzo di 25 $.
1. Aggiungi il prodotto al carrello.
1. Vai al carrello, seleziona il valore $5 **[!UICONTROL Flat Rate shipping]** e applicare il codice coupon.
1. Vai al pagamento, completa la spedizione e passa alla sezione **[!UICONTROL Paytment]** sezione.
1. Torna al carrello.

<u>Risultati previsti</u>:

Non c&#39;è alcun errore relativo all&#39;importo minimo dell&#39;ordine in quanto il totale complessivo di $ 2,4 è maggiore dell&#39;importo richiesto di $ 2.

<u>Risultati effettivi</u>:

* Si è verificato un errore relativo all’importo minimo dell’ordine anche quando il totale complessivo di 2,4 $ è maggiore dell’importo minimo dell’ordine di 2 $.
* Il **[!UICONTROL Continue to Checkout]** è disattivato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
