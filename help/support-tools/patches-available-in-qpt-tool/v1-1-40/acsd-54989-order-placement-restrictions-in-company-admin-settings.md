---
title: "ACSD-54989: l'amministratore della società non può ordinare se [!UICONTROL Enable Purchase Orders] è impostato su Sì e [!UICONTROL Purchase Order] su No"
description: Applicare la patch ACSD-54989 per risolvere il problema Adobe Commerce che impedisce all'amministratore della società di effettuare ordini se [!UICONTROL Enable Purchase Orders] è impostato su Sì e [!UICONTROL Purchase Order] su No.
feature: Orders, Companies, Purchase Orders
role: Admin, Developer
exl-id: c2850409-d310-4681-80ec-af8ba347854c
source-git-commit: 35cd21581ee34a6213be42a79e159439b8856fb6
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-54989: l&#39;amministratore della società non può ordinare se *[!UICONTROL Enable Purchase Orders]* è impostato su *Sì* e *[!UICONTROL Purchase Order]* su *No*

La patch ACSD-54989 risolve il problema che impedisce l&#39;inserimento di ordini se **[!UICONTROL Enable Purchase Orders]** è impostato su *Sì* e **[!UICONTROL Purchase Order]** su *No*. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40. L’ID della patch è ACSD-54989. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p5 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli amministratori della società non possono effettuare ordini se **[!UICONTROL Enable Purchase Orders]** è impostato su *Sì* e **Ordine di acquisto** è impostato su *No*.

<u>Prerequisiti</u>:

Installa [!DNL B2B] moduli.

<u>Passaggi da riprodurre</u>:

1. Abilita la società e lascia [!UICONTROL **Order Approval Configuration]** > **[!UICONTROL Purchase Order**] = *No*.
1. Crea un prodotto semplice al prezzo di 100.
1. Crea una nuova società tramite l’Amministratore.
1. Impostare [!UICONTROL **Abilita ordini di acquisto**] su *Sì*.
1. Accedi come amministratore aziendale sulla vetrina.
1. Aggiungi al carrello il prodotto semplice creato.
1. Passare alla pagina di pagamento e fare clic su **[!UICONTROL Place Order]** per completare l&#39;acquisto.

<u>Risultati previsti</u>:

È possibile effettuare un ordine con successo.

<u>Risultati effettivi</u>:

La pagina **[!UICONTROL My Account]** si apre e l&#39;ordine non viene effettuato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
