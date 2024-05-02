---
title: "ACSD-48694: errore di richiesta di modifica dello stato non valido che impedisce al cliente di effettuare l’ordine"
description: Applica la patch ACSD-48694 per risolvere il problema Adobe Commerce, nel caso in cui l’errore *Richiesta di modifica dello stato non valido* impedisca a un cliente di effettuare un ordine.
exl-id: edf79424-6c4f-4cfd-ab7e-19f95b9bc685
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# ACSD-48694 *È stata richiesta una modifica di stato non valida* l&#39;errore impedisce al cliente di effettuare l&#39;ordine

La patch ACSD-48694 risolve il problema relativo al punto in cui *È stata richiesta una modifica di stato non valida* impedisce a un cliente di effettuare un ordine. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27. L’ID della patch è ACSD-48694. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.37-p4, 2.4.1 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’errore *È stata richiesta una modifica di stato non valida* impedisce a un cliente di effettuare un ordine.

<u>Passaggi da riprodurre</u>:

1. Aggiungi un leggero ritardo durante il `/estimate-shipping-methods` richiesta includendo un `sleep()` a `app/code/Magento/Quote/Model/GuestCart/GuestShippingMethodManagement.php::estimateByExtendedAddress()` funzione, in modo che `/estimate-shipping-methods` richiesta completata dopo il `/shipping-information` quando si passa dalla fase di spedizione alla fase di pagamento durante il pagamento.
1. Configurare la sessione da utilizzare [!DNL Redis] con *disable_locking: 1* impostazione.
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
* L’ordine è stato effettuato correttamente e una *Grazie* viene visualizzata.

<u>Risultati effettivi</u>:

L’errore *È stata richiesta una modifica di stato non valida* viene visualizzato, ma l’ordine viene effettuato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
