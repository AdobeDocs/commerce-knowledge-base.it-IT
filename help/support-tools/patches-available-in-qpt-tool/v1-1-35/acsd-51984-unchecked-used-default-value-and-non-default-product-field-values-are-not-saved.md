---
title: "ACSD-51984: i valori deselezionati [!UICONTROL Use Default Value] e non predefiniti dei campi prodotto non vengono salvati per la seconda visualizzazione sito Web, archivio e archivio"
description: Applica la patch ACSD-51984 per risolvere il problema Adobe Commerce, per cui i valori non selezionati [!UICONTROL Use Default Value] e non predefiniti del campo prodotto non vengono salvati per la seconda visualizzazione del sito Web, dello store e dello store.
feature: Products
role: Admin
exl-id: 1f45c700-dd27-4a69-8634-9c0aa131d197
source-git-commit: f42fcacbe3b7174b2a3571afe80f5eedb8e9aa75
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# ACSD-51984: i valori deselezionati *[!UICONTROL Use Default Value]* e non predefiniti dei campi prodotto non vengono salvati

>[!NOTE]
>
>Questa patch non è aggiornata ed è stata sostituita dalla patch [ACSD-54776](/help/support-tools/patches-available-in-qpt-tool/v1-1-39/acsd-54776-unchecked-used-default-value-and-non-default-product-field-values-are-not-saved.md) aggiunta nella versione 1.1.39 di QPT.

La patch ACSD-51984 risolve il problema per cui i valori non selezionati **[!UICONTROL Use Default Value]** e non predefiniti dei campi prodotto non vengono salvati per la seconda visualizzazione del sito Web, dello store e dello store. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.35. L’ID della patch è ACSD-51984. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I valori *[!UICONTROL Use Default Value]* deselezionati e i valori dei campi prodotto non predefiniti non vengono salvati per la seconda visualizzazione del sito Web, dello store e dello store.

<u>Passaggi da riprodurre</u>:

1. Vai al backend e passa a **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** e crea una nuova visualizzazione per siti web, store e store.
1. Vai a **[!UICONTROL Catalog]** > **[!UICONTROL Products]**, crea un prodotto semplice e salvalo, quindi assegna il prodotto a entrambi i siti Web, da **[!UICONTROL Product in Websites]**.
1. Modificare l&#39;ambito nella visualizzazione archivio appena creata dal passaggio 2.
1. Vai a **[!UICONTROL Search Engine Optimization]** e deseleziona le caselle di controllo **[!UICONTROL Use Default Value]** per [!UICONTROL Meta Title], [!UICONTROL Meta Keywords] e [!UICONTROL Meta Description].
1. Pulire il testo dai campi *[!UICONTROL Meta Title]*, *[!UICONTROL Meta Keywords]* e *[!UICONTROL Meta Description]* e fare clic su **[!UICONTROL Save]**.
1. Passa di nuovo a **[!UICONTROL Search Engine Optimization]**.

<u>Risultati previsti</u>

I valori per i campi e per le caselle di controllo vengono salvati.

<u>Risultati effettivi</u>

I valori dei campi e delle caselle di controllo non vengono salvati.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) nella guida di [!DNL Quality Patches Tool].