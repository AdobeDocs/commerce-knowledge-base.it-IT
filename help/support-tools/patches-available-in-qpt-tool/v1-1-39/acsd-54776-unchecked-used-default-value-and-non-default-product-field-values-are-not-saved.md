---
title: '"ACSD-54776: non selezionato [!UICONTROL Use Default Value] e i valori dei campi prodotto non predefiniti non vengono salvati per la seconda visualizzazione sito Web, store e store.'
description: Applica la patch ACSD-54776 per risolvere il problema di Adobe Commerce in cui [!UICONTROL Use Default Value] e i valori dei campi prodotto non predefiniti non vengono salvati per la seconda visualizzazione sito Web, store e store.
feature: Products
role: Admin, Developer
exl-id: 5bdad804-8d7b-48b4-ba3b-c2d5387ef55e
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-54776: non selezionato *[!UICONTROL Use Default Value]* I valori dei campi prodotto predefiniti e non non vengono salvati

>[!NOTE]
>
>Questa patch sostituisce la [ACSD-51984](/help/support-tools/patches-available-in-qpt-tool/v1-1-35/acsd-51984-unchecked-used-default-value-and-non-default-product-field-values-are-not-saved.md) patch rilasciata in QPT 1.1.35.

La patch ACSD-54776 risolve il problema in cui l&#39;opzione **[!UICONTROL Use Default Value]** e i valori dei campi prodotto non predefiniti non vengono salvati per la seconda visualizzazione sito Web, store e store. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.39. L’ID della patch è ACSD-54776. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.5-p4, 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Deselezionato *[!UICONTROL Use Default Value]* e i valori dei campi prodotto non predefiniti non vengono salvati per la seconda visualizzazione sito Web, store e store.

<u>Passaggi da riprodurre</u>:

1. Vai al backend e passa a **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** e creare una nuova visualizzazione per siti web, store e store.
1. Vai a **[!UICONTROL Catalog]** > **[!UICONTROL Products]**, crea un prodotto semplice e salvalo e assegna il prodotto a entrambi i siti web da **[!UICONTROL Product in Websites]**.
1. Modificare l&#39;ambito nella visualizzazione archivio appena creata dal passaggio 2.
1. Vai a **[!UICONTROL Search Engine Optimization]** e deseleziona la **[!UICONTROL Use Default Value]** caselle di controllo per [!UICONTROL Meta Title], [!UICONTROL Meta Keywords], e [!UICONTROL Meta Description].
1. Rimuovi testo dai campi: *[!UICONTROL Meta Title]*, *[!UICONTROL Meta Keywords]* e *[!UICONTROL Meta Description]* e fai clic su **[!UICONTROL Save]**.
1. Vai a **[!UICONTROL Search Engine Optimization]** di nuovo.

<u>Risultati previsti</u>

I valori dei campi e delle caselle di controllo vengono salvati.

<u>Risultati effettivi</u>

I valori dei campi e delle caselle di controllo non vengono salvati.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) nel [!DNL Quality Patches Tool] guida.
