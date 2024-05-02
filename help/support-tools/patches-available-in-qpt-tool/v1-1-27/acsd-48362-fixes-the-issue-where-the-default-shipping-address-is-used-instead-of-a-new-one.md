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

La patch ACSD-48362 risolve il problema relativo all&#39;utilizzo dell&#39;indirizzo di spedizione predefinito al posto dell&#39;indirizzo appena aggiunto quando si effettua un ordine utilizzando un preventivo negoziabile. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27. L’ID della patch è ACSD-48362. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.1 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;indirizzo di spedizione predefinito viene utilizzato al posto dell&#39;indirizzo di spedizione appena aggiunto quando si effettua un ordine utilizzando un preventivo negoziabile.

<u>Passaggi da riprodurre</u>:

1. Abilitare l’offerta B2B passando a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B features]** > **[!UICONTROL Enable company]** > **[!UICONTROL Enable B2B quote]**.
1. Accedi come utente aziendale.
1. Aggiungi un prodotto al carrello.
1. Vai alla pagina del carrello e richiedi un preventivo.
1. Vai a **[!UICONTROL My Quotes]** e selezionare il preventivo appena creato.
1. Vai a **[!UICONTROL Shipping Information]** sezione della pagina dell&#39;offerta del cliente.
   * Clic **[!UICONTROL Add New Address]**, compila il modulo e salva l&#39;indirizzo (non selezionare **[!UICONTROL Use as my default billing address]** o **[!UICONTROL Use as my default shipping address]**).
1. Clic **[!UICONTROL Send for Review]** nella pagina dell&#39;offerta del cliente.
1. Vai all’amministratore di Adobe Commerce come utente amministratore, apri il preventivo appena creato e fai clic su **[!UICONTROL Send]**.
1. Ora vai alla pagina dell’offerta del cliente, aggiorna la pagina e fai clic su **[!UICONTROL Proceed to Checkout]**.
1. Nella pagina di pagamento, i dati mostrano l&#39;indirizzo di spedizione predefinito anche quando viene selezionato il nuovo indirizzo di spedizione.
1. Clic **[!UICONTROL Continue]** e ordina.

<u>Risultati previsti</u>:

L&#39;ordine deve utilizzare il nuovo indirizzo senza selezionare nuovamente l&#39;indirizzo di spedizione predefinito nella pagina di pagamento.

<u>Risultati effettivi</u>:

L&#39;ordine viene effettuato con l&#39;indirizzo di spedizione predefinito.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud. 

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
