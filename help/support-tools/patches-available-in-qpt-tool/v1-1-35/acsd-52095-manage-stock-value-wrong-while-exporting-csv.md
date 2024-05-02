---
title: "ACSD-52095: errore durante l’esportazione del file CSV durante la gestione del valore delle azioni"
description: Applica la patch ACSD-52095 per risolvere il problema Adobe Commerce in cui il valore delle azioni di gestione del prodotto non è corretto durante l’esportazione del file CSV.
feature: Inventory, Products
role: Admin, Developer
exl-id: 9e599931-e9b1-4216-b78d-3993d9c3132d
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-52095 [!UICONTROL Manage Stock] valore errato durante l’esportazione del file CSV

La patch ACSD-52095 risolve il problema in cui il `manage_stock` valore errato durante l’esportazione del file CSV. Questa patch è disponibile quando [!DNL Quality Patches Tool (QPT)] 1.1.35. L’ID della patch è ACSD-52095. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.5-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il `manage_stock` Il valore viene impostato in modo errato su 0 nel file CSV dopo l’esportazione del prodotto.

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** e imposta **[!UICONTROL Manage Stock]** = *[!UICONTROL No]*.
1. Crea un nuovo prodotto e salvalo.
1. Vai a **[!UICONTROL System]** > **[!UICONTROL Export]**.
1. Seleziona *[!UICONTROL Entity Type]* = *[!UICONTROL Products]* ed esportare i prodotti.
1. Controlla il file CSV generato: `manage_stock` = 0 `use_config_manage_stock` = 1.
1. Vai di nuovo a **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]**, e impostare  **[!UICONTROL Manage Stock]** = *[!UICONTROL Yes]*.
1. Vai a **Sistema** > **Esporta**.
Seleziona *[!UICONTROL Entity Type]* = *[!UICONTROL Products and export the products]*.
1. Controlla il file CSV generato: `manage_stock` = 0 `use_config_manage_stock` = 1.
1. Apri il prodotto nell’Admin, vai a **[!UICONTROL Advanced Inventory]** e controlla **[!UICONTROL Manage Stock]** valore.

<u>Risultati previsti</u>

Il **[!UICONTROL Manage Stock]** il valore è *1* quando è abilitato per i prodotti.

<u>Risultati effettivi</u>

Il **[!UICONTROL Manage Stock]** il valore è *0* quando è abilitato per i prodotti.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) nel [!DNL Quality Patches Tool] guida.
