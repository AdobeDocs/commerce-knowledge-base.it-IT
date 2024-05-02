---
title: '"49843 ACSD: collegamento per il download del prodotto non disponibile dopo la fatturazione automatica con [!UICONTROL Payment Action] = [!UICONTROL Intent Sale]'''
description: Applicare la patch ACSD-49843 per risolvere il problema Adobe Commerce in cui il collegamento di download del prodotto non è disponibile dopo la fatturazione automatica dell'articolo ordinato tramite un metodo di pagamento online quando [!UICONTROL Payment Action] è impostato su [!UICONTROL Intent Sale].
feature: Catalog Management, Configuration, Invoices, Orders, Storefront
role: Admin, Developer
exl-id: 4bfa3827-a2b1-4168-a39c-99c617ee4795
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# ACSD-49843: collegamento per il download del prodotto non disponibile dopo la fatturazione automatica con [!UICONTROL Payment Action] = [!UICONTROL Intent Sale]

La patch ACSD-49843 risolve il problema relativo all&#39;indisponibilità del collegamento di download del prodotto dopo la fatturazione automatica dell&#39;articolo ordinato con un metodo di pagamento online quando [!UICONTROL Payment Action] è impostato su [!UICONTROL Intent Sale]. Questa patch è disponibile quando [!DNL Quality Patches Tool (QPT)] 1.1.37. L’ID della patch è ACSD-49843. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.3.7-p4, 2.4.1 - 2.4.6-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il collegamento per il download del prodotto non è disponibile dopo la fatturazione automatica dell&#39;articolo ordinato con un metodo di pagamento online quando [!UICONTROL Payment Action] è impostato su [!UICONTROL Intent Sale].

<u>Passaggi da riprodurre</u>:

1. Accedi all’amministratore di Adobe Commerce e passa a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Configure Braintree]**.

   * In [!UICONTROL Payment Action] a discesa, seleziona **[!UICONTROL Intent Sale]**, e impostare *[!UICONTROL Enable Card Payments]* a *Sì*.

1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Downloadable Product Option]** > **[!UICONTROL Order Item status for Download]**, e assicurati che sia impostato su *&quot;Fatturato&quot;*.
1. Nella vetrina, accedi come cliente.

   * Aggiungi al carrello qualsiasi prodotto scaricabile e un prodotto semplice.
   * Utilizzare [!DNL Braintree Pay] per effettuare l’ordine utilizzando l’opzione scheda.

1. Vai a **[!UICONTROL My Orders]** e verificare che la fattura venga creata automaticamente per l&#39;ordine e che entrambi gli stati degli articoli siano *&quot;Fatturato&quot;*.
1. Vai a **[!UICONTROL My Downloadable Products]** e osserva che il collegamento per il download non è ancora disponibile.
1. In Amministratore, vai a tale ordine e crea una spedizione per esso.
1. Nella vetrina, vai a **[!UICONTROL My Downloadable Products]** e osserva che il collegamento per il download è ora disponibile.

<u>Risultati previsti</u>:

Il collegamento di download è disponibile quando lo stato del prodotto scaricabile è *&quot;Fatturato&quot;*.

<u>Risultati effettivi</u>:

Il collegamento di download non è disponibile anche quando lo stato del prodotto scaricabile indica *&quot;Fatturato&quot;*. È disponibile solo dopo la creazione di una spedizione per il prodotto fisico.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
