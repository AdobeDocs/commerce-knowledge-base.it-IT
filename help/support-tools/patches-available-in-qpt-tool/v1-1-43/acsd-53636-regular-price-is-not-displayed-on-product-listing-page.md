---
title: "ACSD-53636: il prezzo normale non viene visualizzato nella pagina [!UICONTROL Product Listing]"
description: Applicare la patch ACSD-53636 per risolvere il problema di Adobe Commerce, in cui il prezzo normale non viene visualizzato nelle pagine *[!UICONTROL Product Listing]* per i prodotti configurabili con prodotti secondari a prezzi speciali.
feature: Catalog Management, Products
role: Admin, Developer
exl-id: 97b4eb64-92d1-4db1-8e5b-915b16115663
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# ACSD-53636: il prezzo normale non viene visualizzato nella pagina *[!UICONTROL Product Listing]*

La patch ACSD-53636 risolve il problema che non consente la visualizzazione del prezzo normale nelle pagine *[!UICONTROL Product Listing]* per i prodotti configurabili con prodotti secondari a prezzi speciali. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43. L’ID della patch è ACSD-53636. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.4-p6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il prezzo normale non viene visualizzato nelle pagine *[!UICONTROL Product Listing]* per i prodotti configurabili che hanno prodotti secondari con prezzi speciali.

<u>Passaggi da riprodurre</u>:

1. Accedi all&#39;amministratore e vai a **[!UICONTROL Admin]** > **[!UICONTROL Catalog]**, quindi crea o apri qualsiasi prodotto configurabile.
2. Apri il prodotto secondario e aggiungi un prezzo speciale a tutti o a uno dei prodotti secondari e salva il prodotto.
3. Vai a front-end e apri la pagina **[!UICONTROL Product Detail]** del prodotto configurabile; sui campioni del prodotto secondario con prezzo speciale, vedrai *[!UICONTROL Regular price]* barrato (previsto).
4. Vai a front-end e apri la pagina **[!UICONTROL Product Listing]** per il prodotto configurabile con prezzo speciale; vedi che le modifiche al campione di prodotto configurabile non visualizzano il prezzo regolare a differenza di *[!UICONTROL Product Detail Page]* e altri prodotti semplici.

<u>Risultati previsti</u>:

Nella pagina *[!UICONTROL Product Listing]*, il prodotto configurabile mostra il prezzo regolare per il suo prodotto secondario.

<u>Risultati effettivi</u>:

Nella pagina *[!UICONTROL Product Listing]*, il prodotto configurabile non mostra il prezzo regolare per il suo prodotto secondario.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
