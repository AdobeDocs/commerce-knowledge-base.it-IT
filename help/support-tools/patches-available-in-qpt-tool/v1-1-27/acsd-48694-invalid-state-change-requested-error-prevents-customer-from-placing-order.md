---
title: 'ACSD-48694: errore richiesto di modifica dello stato non valido che impedisce al cliente di effettuare l''ordine'
description: Applica la patch ACSD-48694 per risolvere il problema Adobe Commerce, nel caso in cui l’errore *Richiesta di modifica dello stato non valido* impedisca a un cliente di effettuare un ordine.
exl-id: edf79424-6c4f-4cfd-ab7e-19f95b9bc685
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# ACSD-48694: *Richiesta di modifica dello stato non valida* errore che impedisce al cliente di effettuare l&#39;ordine

La patch ACSD-48694 risolve il problema che impediva a un cliente di effettuare un ordine a causa dell&#39;errore *Richiesta di modifica dello stato non valido*. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27. L’ID della patch è ACSD-48694. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.37-p4, 2.4.1 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Errore *Richiesta di modifica dello stato non valida* che impedisce a un cliente di effettuare un ordine.

<u>Passaggi da riprodurre</u>:

1. Aggiungere un leggero ritardo durante la richiesta `/estimate-shipping-methods` includendo una funzione `sleep()` in `app/code/Magento/Quote/Model/GuestCart/GuestShippingMethodManagement.php::estimateByExtendedAddress()`, in modo che la richiesta `/estimate-shipping-methods` venga completata dopo il `/shipping-information` quando si passa dalla fase di spedizione alla fase di pagamento durante l&#39;estrazione.
1. Configurare la sessione per l&#39;utilizzo di [!DNL Redis] con l&#39;impostazione *disable_locking: 1*.
1. Apri **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** e abilita *[!UICONTROL Persistent Shopping Cart]*.
1. Accedi come cliente e aggiungi un prodotto al carrello.
1. Lascia scadere la sessione del cliente. Il cookie persistente e il carrello persistono ancora.
1. Ora vai al pagamento, aggiungi l&#39;indirizzo di spedizione e passa alla sezione del pagamento.
1. Torna alla home page o a qualsiasi altra pagina e accedi con l’account del cliente.
1. Fai scadere di nuovo la sessione.
1. Ora vai direttamente alla pagina di pagamento e passa alla fase di pagamento.
1. Provi ad effettuare l&#39;ordine.

<u>Risultati previsti</u>:

* Nessun errore.
* L&#39;ordine è stato effettuato e viene visualizzata una pagina di *ringraziamento*.

<u>Risultati effettivi</u>:

Errore *È stata richiesta una modifica dello stato non valida*, ma l&#39;ordine è stato effettuato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
