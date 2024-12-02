---
title: '49843 ACSD: collegamento per il download del prodotto non disponibile dopo la fatturazione automatica con [!UICONTROL Payment Action] = [!UICONTROL Intent Sale]'
description: Applicare la patch ACSD-49843 per risolvere il problema di Adobe Commerce in cui il collegamento di download del prodotto non è disponibile dopo la fatturazione automatica dell'articolo ordinato tramite un metodo di pagamento online quando [!UICONTROL Payment Action] è impostato su [!UICONTROL Intent Sale].
feature: Catalog Management, Configuration, Invoices, Orders, Storefront
role: Admin, Developer
exl-id: 4bfa3827-a2b1-4168-a39c-99c617ee4795
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# ACSD-49843: collegamento per il download del prodotto non disponibile dopo la fatturazione automatica con [!UICONTROL Payment Action] = [!UICONTROL Intent Sale]

La patch ACSD-49843 risolve il problema relativo alla mancata disponibilità del collegamento di download del prodotto dopo la fatturazione automatica dell&#39;articolo ordinato tramite un metodo di pagamento online quando [!UICONTROL Payment Action] è impostato su [!UICONTROL Intent Sale]. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.37. L’ID della patch è ACSD-49843. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.3.7-p4, 2.4.1 - 2.4.6-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il collegamento di download del prodotto non è disponibile dopo la fatturazione automatica dell&#39;articolo ordinato tramite un metodo di pagamento online quando [!UICONTROL Payment Action] è impostato su [!UICONTROL Intent Sale].

<u>Passaggi da riprodurre</u>:

1. Accedi all&#39;amministratore di Adobe Commerce e passa a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Configure Braintree]**.

   * Nel menu a discesa [!UICONTROL Payment Action], selezionare **[!UICONTROL Intent Sale]** e impostare *[!UICONTROL Enable Card Payments]* su *Sì*.

1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Downloadable Product Option]** > **[!UICONTROL Order Item status for Download]** e assicurati che sia impostato su *&quot;Fatturato&quot;*.
1. Nella vetrina, accedi come cliente.

   * Aggiungi al carrello qualsiasi prodotto scaricabile e un prodotto semplice.
   * Utilizza [!DNL Braintree Pay] per effettuare l&#39;ordine utilizzando l&#39;opzione della scheda.

1. Andare a **[!UICONTROL My Orders]** e verificare che la fattura sia creata automaticamente per l&#39;ordine e che entrambi gli stati dell&#39;articolo siano *&quot;Fatturati&quot;*.
1. Vai a **[!UICONTROL My Downloadable Products]** e osserva che il collegamento per il download non è ancora disponibile.
1. In Amministratore, vai a tale ordine e crea una spedizione per esso.
1. Nella vetrina, vai a **[!UICONTROL My Downloadable Products]** e osserva che il collegamento per il download è ora disponibile.

<u>Risultati previsti</u>:

Il collegamento di download è disponibile quando lo stato del prodotto scaricabile è *&quot;Fatturato&quot;*.

<u>Risultati effettivi</u>:

Il collegamento di download non è disponibile anche quando lo stato del prodotto scaricabile indica *&quot;Fatturato&quot;*. È disponibile solo dopo la creazione di una spedizione per il prodotto fisico.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
