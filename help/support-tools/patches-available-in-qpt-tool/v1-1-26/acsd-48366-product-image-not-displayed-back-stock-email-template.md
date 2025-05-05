---
title: 'ACSD-48366: immagine del prodotto non visualizzata nel modello e-mail [!UICONTROL Back to Stock]'
description: Applica la patch ACSD-48366 per risolvere il problema Adobe Commerce, se l’immagine della miniatura del prodotto non viene visualizzata nell’e-mail di avviso sulle scorte del prodotto.
exl-id: 57b549b0-6e97-4d5f-927e-9585f3257872
feature: Admin Workspace, Communications, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-48366: immagine del prodotto non visualizzata nel modello e-mail [!UICONTROL Back to Stock]

La patch ACSD-48366 risolve il problema se l’immagine della miniatura del prodotto non viene visualizzata nell’e-mail di avviso sul magazzino del prodotto. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26. L’ID della patch è ACSD-48366. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;immagine del prodotto non è visualizzata nel modello di e-mail [!UICONTROL Back to Stock].

<u>Passaggi da riprodurre</u>:

1. Abilita *[!UICONTROL Product Alert]* per *[!UICONTROL Back in Stock]* andando in **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Alert]** > **[!UICONTROL Allow Alert When Product Comes Back in Stock]** = *[!UICONTROL Yes]*.
1. Abilita *[!UICONTROL Display Out of Stock Products]* andando in **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Display Out of Stock]** = *[!UICONTROL Yes]*.
1. Creare un prodotto semplice con qtà = 0.
1. Crea un cliente dalla vetrina e abbonati al prodotto di cui sopra per ricevere avvisi sui prodotti quando sono in magazzino.
1. Prepara il prodotto in magazzino.
1. Esegui il cron di avviso del prodotto.

   ```
   n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

1. Avvia l’avviso prodotto per il cliente.

   ```
   bin/magento queue:consumers:start product_alert
   ```

1. Controlla l’e-mail. L’e-mail di avviso sul titolo ora dovrebbe essere disponibile nel dispositivo di raccolta della posta.

<u>Risultati previsti</u>:

L’immagine del prodotto viene visualizzata nell’e-mail di avviso sulle scorte.

<u>Risultati effettivi</u>:

L’immagine del prodotto non è disponibile nell’e-mail di avviso sulle scorte.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
