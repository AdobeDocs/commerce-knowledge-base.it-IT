---
title: "ACSD-48362: viene utilizzato l’indirizzo di spedizione predefinito anziché uno nuovo."
description: Applicare la patch ACSD-48362 per risolvere il problema Adobe Commerce in cui viene utilizzato l'indirizzo di spedizione predefinito anziché uno nuovo quando si effettua un ordine utilizzando un preventivo negoziabile.
exl-id: 52f518b6-6f73-42cc-ac1b-c893cd5007fa
feature: Admin Workspace, B2B, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# ACSD-48362: viene utilizzato l’indirizzo di spedizione predefinito anziché uno nuovo

La patch ACSD-48362 risolve il problema relativo all&#39;utilizzo dell&#39;indirizzo di spedizione predefinito al posto dell&#39;indirizzo appena aggiunto quando si effettua un ordine utilizzando un preventivo negoziabile. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27. L’ID della patch è ACSD-48362. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.1 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;indirizzo di spedizione predefinito viene utilizzato al posto dell&#39;indirizzo di spedizione appena aggiunto quando si effettua un ordine utilizzando un preventivo negoziabile.

<u>Passaggi da riprodurre</u>:

1. Abilitare le virgolette B2B passando a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B features]** > **[!UICONTROL Enable company]** > **[!UICONTROL Enable B2B quote]**.
1. Accedi come utente aziendale.
1. Aggiungi un prodotto al carrello.
1. Vai alla pagina del carrello e richiedi un preventivo.
1. Andare alla pagina **[!UICONTROL My Quotes]** del cliente e selezionare il preventivo appena creato.
1. Passare alla sezione **[!UICONTROL Shipping Information]** della pagina dell&#39;offerta del cliente.
   * Fare clic su **[!UICONTROL Add New Address]**, compilare il modulo e salvare l&#39;indirizzo (non selezionare **[!UICONTROL Use as my default billing address]** o **[!UICONTROL Use as my default shipping address]**).
1. Fare clic su **[!UICONTROL Send for Review]** nella pagina del preventivo del cliente.
1. Accedere all&#39;amministratore di Adobe Commerce come utente amministratore, aprire il preventivo appena creato e fare clic su **[!UICONTROL Send]**.
1. Passare alla pagina dell&#39;offerta del cliente, aggiornare la pagina e fare clic su **[!UICONTROL Proceed to Checkout]**.
1. Nella pagina di pagamento, i dati mostrano l&#39;indirizzo di spedizione predefinito anche quando viene selezionato il nuovo indirizzo di spedizione.
1. Fare clic su **[!UICONTROL Continue]** e ordinare.

<u>Risultati previsti</u>:

L&#39;ordine deve utilizzare il nuovo indirizzo senza selezionare nuovamente l&#39;indirizzo di spedizione predefinito nella pagina di pagamento.

<u>Risultati effettivi</u>:

L&#39;ordine viene effettuato con l&#39;indirizzo di spedizione predefinito.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud. 

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
