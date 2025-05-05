---
title: "ACSD-46770: l'e-mail di conferma dell'ordine viene inviata anche quando [!UICONTROL Email Order Confirmation] è deselezionato"
description: Applicare la patch ACSD-46770 per risolvere il problema di Adobe Commerce, per cui le e-mail di conferma dell'ordine vengono inviate anche quando [!UICONTROL Email Order Confirmation] non è selezionato.
exl-id: 9cbf3a57-1f59-4030-b432-0e6cad410a27
feature: Communications, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-46770: l&#39;e-mail di conferma dell&#39;ordine viene inviata anche quando **[!UICONTROL Email Order Confirmation]** è deselezionato

La patch ACSD-46770 risolve il problema che consente di effettuare ordini tramite API REST come utente guest anche quando **[!UICONTROL Email Order Confirmation]** non è selezionato. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24. L’ID della patch è ACSD-46770. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Viene inviata un&#39;e-mail di conferma dell&#39;ordine anche quando **[!UICONTROL Email Order Confirmation]** non è selezionato.

<u>Passaggi da riprodurre</u>:

1. Crea un account cliente.
1. Vai a **[!UICONTROL Sales]** > **[!UICONTROL Order]** e fai clic su **[!UICONTROL Create New Order]**.
1. Selezionare il cliente, aggiungere i prodotti all&#39;ordine, inserire l&#39;indirizzo e selezionare i metodi di spedizione e di pagamento.
1. Prima di inviare l&#39;ordine, deselezionare la casella di controllo **[!UICONTROL Email Order confirmation]**.
1. Fai clic su **[!UICONTROL Submit Order]** per creare l&#39;ordine.

<u>Risultati previsti</u>:

Non inviare un&#39;e-mail di conferma dell&#39;ordine se **[!UICONTROL Email Order Confirmation]** non è selezionato.

<u>Risultati effettivi</u>:

Un&#39;e-mail di conferma dell&#39;ordine viene inviata indipendentemente dalla casella di controllo **[!UICONTROL Email Order Confirmation]** non selezionata.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
