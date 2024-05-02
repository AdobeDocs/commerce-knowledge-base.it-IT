---
title: "ACSD-49706: valore predefinito salvato per l’attributo campione visivo quando non è selezionato alcun valore"
description: Applicate la patch ACSD-49706 per risolvere il problema Adobe Commerce, se per un attributo di campione visivo non è selezionato alcun valore, in cui viene salvato un valore predefinito.
exl-id: fe6071df-f2a4-443a-acfa-67f3d253c5e4
feature: Admin Workspace, Attributes
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# ACSD-49706: valore predefinito salvato per l’attributo campione visivo quando non è selezionato alcun valore

La patch ACSD-49706 risolve il problema relativo al salvataggio di un valore predefinito per un attributo di campione visivo quando non viene selezionato alcun valore. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29. L’ID della patch è ACSD-49706. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Se non è selezionato alcun valore, viene salvato un valore predefinito per un attributo di campione visivo.

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**.
1. Clic **[!UICONTROL Add New Attribute]**.
1. Compila i campi.

   * Ad esempio, scegli il tipo di input *[!UICONTROL Visual Swatch]* e aggiungere più opzioni (ad esempio *Rosso*, *Verde*). Assicurati di scegliere una di queste opzioni come predefinita.
   * Clic **[!UICONTROL Save Attribute]**.

1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]**.
1. Modifica il *[!UICONTROL Default]* set di attributi.
1. Sposta *[!UICONTROL New Attribute]* dalla colonna *[!UICONTROL Unassigned Attributes]* al *[!UICONTROL Product Details]* nella colonna centrale.

   * Clic **[!UICONTROL Save]**.

1. Creare un nuovo prodotto utilizzando *[!UICONTROL Default]* set di attributi.

   * Lascia *[!UICONTROL New Attribute]* vuoto e salvalo.

1. Una volta salvato, viene visualizzato un valore in *[!UICONTROL New Attribute]*.

<u>Risultati previsti</u>:

Nessun valore assegnato a *[!UICONTROL New Attribute]* per impostazione predefinita.

<u>Risultati effettivi</u>:

All’attributo viene applicato un valore predefinito al momento del salvataggio di un prodotto.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
