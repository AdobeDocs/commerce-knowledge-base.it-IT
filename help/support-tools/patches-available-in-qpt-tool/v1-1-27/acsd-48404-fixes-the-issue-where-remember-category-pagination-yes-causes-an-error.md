---
title: "ACSD-48404: *[!UICONTROL Remember Category Pagination] = [!UICONTROL Yes]* causa un errore quando si preme il pulsante Indietro del browser"
description: Applica la patch ACSD-48404 per risolvere il problema di Adobe Commerce per cui *[!UICONTROL Remember Category Pagination] = [!UICONTROL Yes]* causa un errore quando si preme il pulsante Indietro del browser.
exl-id: b4b96198-dee6-4b3c-b60a-0983ef8ef7b2
feature: Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-48404: *[!UICONTROL Remember Category Pagination]=[!UICONTROL Yes]* causa un errore quando si preme il pulsante Indietro del browser

La patch ACSD-48404 risolve il problema se *[!UICONTROL Remember Category Pagination]=[!UICONTROL Yes]* causa un errore quando si preme il pulsante Indietro del browser. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27. L’ID della patch è ACSD-48404. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

*[!UICONTROL Remember Category Pagination]=[!UICONTROL Yes]* causa un errore quando si preme il pulsante Indietro del browser.


<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Storefront]** e imposta *[!UICONTROL Remember Category Pagination]* su *Sì*.
1. Apri una categoria nella vetrina.
1. Selezionare un valore non predefinito nel menu a discesa *[!UICONTROL Show Per Page]*. Dopo aver selezionato un’opzione, la pagina viene ricaricata.
1. Una volta ricaricata la pagina, fai clic su qualsiasi prodotto nella pagina del catalogo.
1. Nella pagina dei dettagli del prodotto aperta, fare clic sul pulsante **[!UICONTROL Back]** del browser.

<u>Risultati previsti</u>:

La pagina del catalogo viene nuovamente aperta.

<u>Risultati effettivi</u>:

La pagina della categoria restituisce un errore.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
