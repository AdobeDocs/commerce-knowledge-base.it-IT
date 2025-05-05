---
title: 'ACSD-49042: prodotto con ordine infinito non può essere ordinato dalla vetrina'
description: Applica la patch ACSD-49042 per risolvere il problema di Adobe Commerce, a causa del quale non è possibile ordinare un prodotto con ordine inevaso dalla vetrina.
exl-id: b9227296-f300-447c-a241-30ccc0691c9a
feature: Admin Workspace, Orders, Products, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-49042: prodotto con ordine infinito non può essere ordinato dalla vetrina

La patch ACSD-49042 risolve il problema che impediva di ordinare dalla vetrina un prodotto con ordine infinito. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27. L’ID della patch è ACSD-49042. Il problema è stato risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.4-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’errore si verifica quando un prodotto con ordine inevaso infinito non può essere ordinato dalla vetrina.

<u>Passaggi da riprodurre</u>:

1. Imposta le seguenti impostazioni di configurazione:
   * **[!UICONTROL Display Out of Stock Products]** impostato su *[!UICONTROL Yes]*.
   * **[!UICONTROL Backorders]** impostato su *[!UICONTROL Allow Qty Below 0]*.
1. Aggiungi un nuovo **[!DNL custom stock]** e **[!DNL custom source]**.
1. Assegnare un prodotto a **[!DNL custom source]** e assicurarsi che sia impostato un numero di inventario (ad esempio: *10*).
1. Nella pagina di modifica del prodotto aprire **[!UICONTROL Advanced Inventory]**. Imposta **[!UICONTROL minimum quantity]** nel carrello, (ad esempio: *160*). La quantità deve essere superiore al magazzino.
1. Vai alla vetrina e acquista un prodotto per creare una prenotazione.
1. Cambia **[!UICONTROL product quantity]** in *0*. Il punto critico è salvare il prodotto da **[!DNL Admin panel]** quando è presente una prenotazione.
1. Apri **[!UICONTROL product page]** nella vetrina e prova ad aggiungere il prodotto al carrello.

<u>Risultati previsti</u>:

È possibile aggiungere il prodotto al carrello perché sono consentiti ordini inevasi per una quantità inferiore a *0*.

<u>Risultati effettivi</u>:

Il prodotto è esaurito.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
