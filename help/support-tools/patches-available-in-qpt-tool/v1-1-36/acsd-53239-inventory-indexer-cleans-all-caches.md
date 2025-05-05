---
title: "ACSD-53239: l’indicizzatore del magazzino pulisce tutte le cache"
description: Applicare la patch ACSD-53239 per risolvere il problema di Adobe Commerce in cui l'indicizzatore inventario pulisce tutte le cache in modalità [!UICONTROL Update on Schedule].
feature: GraphQL, Inventory, Catalog Management
role: Admin, Developer
exl-id: b8e68cf7-d326-4c9e-8749-d83113de2070
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# ACSD-53239: l&#39;indicizzatore inventario pulisce tutte le cache in modalità [!UICONTROL Update on Schedule]

La patch ACSD-53239 risolve il problema relativo alla pulizia di tutte le cache da parte dell&#39;indicizzatore inventario in modalità [!UICONTROL Update on Schedule]. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.36. L’ID della patch è ACSD-53239. Il problema è stato risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.5-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;indicizzatore inventario pulisce tutte le cache in modalità [!UICONTROL Update on Schedule].

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL Admin]** > **[!UICONTROL Catalog Products]** e seleziona circa *1200* prodotti.
2. Aggiornare *[!UICONTROL Qty]* a un nuovo valore e fare clic su **[!UICONTROL Save]**.
3. Esegui `bin/magento cron:run` immediatamente dopo il salvataggio.
4. Esegui la seguente query GraphQL:

   ```GraphQL
   {
     storeConfig {
     absolute_footer
     }
   }
   ```

<u>Risultati previsti</u>

La query viene elaborata nell’arco del tempo consueto.

<u>Risultati effettivi</u>

La query viene elaborata insolitamente lentamente.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
