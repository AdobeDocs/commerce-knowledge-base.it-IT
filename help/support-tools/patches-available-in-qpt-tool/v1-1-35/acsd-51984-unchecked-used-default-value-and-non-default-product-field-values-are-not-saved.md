---
title: '"ACSD-51984: non selezionato [!UICONTROL Use Default Value] e i valori dei campi prodotto non predefiniti non vengono salvati per la seconda visualizzazione sito Web, store e store.'
description: Applica la patch ACSD-51984 per risolvere il problema di Adobe Commerce in cui [!UICONTROL Use Default Value] e i valori dei campi prodotto non predefiniti non vengono salvati per la seconda visualizzazione sito Web, store e store.
feature: Products
role: Admin
exl-id: 1f45c700-dd27-4a69-8634-9c0aa131d197
source-git-commit: f42fcacbe3b7174b2a3571afe80f5eedb8e9aa75
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# ACSD-51984: non selezionato *[!UICONTROL Use Default Value]* I valori dei campi prodotto predefiniti e non non vengono salvati

>[!NOTE]
>
>Questa patch non è aggiornata ed è stata sostituita dalla [ACSD-54776](/help/support-tools/patches-available-in-qpt-tool/v1-1-39/acsd-54776-unchecked-used-default-value-and-non-default-product-field-values-are-not-saved.md) patch aggiunta nella versione 1.1.39 di QPT.

La patch ACSD-51984 risolve il problema in cui l&#39;opzione **[!UICONTROL Use Default Value]** e i valori dei campi prodotto non predefiniti non vengono salvati per la seconda visualizzazione sito Web, store e store. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.35. L’ID della patch è ACSD-51984. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Deselezionato *[!UICONTROL Use Default Value]* e i valori dei campi prodotto non predefiniti non vengono salvati per la seconda visualizzazione sito Web, store e store.

<u>Passaggi da riprodurre</u>:

1. Vai al backend e passa a **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** e creare una nuova visualizzazione per siti web, store e store.
1. Vai a **[!UICONTROL Catalog]** > **[!UICONTROL Products]**, crea un prodotto semplice e salvalo e assegna il prodotto a entrambi i siti web, dal **[!UICONTROL Product in Websites]**.
1. Modificare l&#39;ambito nella visualizzazione archivio appena creata dal passaggio 2.
1. Vai a **[!UICONTROL Search Engine Optimization]** e deseleziona la **[!UICONTROL Use Default Value]** caselle di controllo per [!UICONTROL Meta Title], [!UICONTROL Meta Keywords], e [!UICONTROL Meta Description].
1. Rimuovi testo dai campi: *[!UICONTROL Meta Title]*, *[!UICONTROL Meta Keywords]* e *[!UICONTROL Meta Description]* e fai clic su **[!UICONTROL Save]**.
1. Vai a **[!UICONTROL Search Engine Optimization]** di nuovo.

<u>Risultati previsti</u>

I valori per i campi e per le caselle di controllo vengono salvati.

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