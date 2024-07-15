---
title: 'ACSD-49835: la casella di controllo [!UICONTROL Use Default Value] non è salvata'
description: Applicare la patch ACSD-49835 per risolvere il problema di Adobe Commerce in cui la casella di controllo [!UICONTROL Use Default Value] non viene salvata correttamente a livello di archivio per un attributo a selezione multipla.
exl-id: 84270551-c8a9-4b08-a055-ffdcc538c33d
feature: Storefront
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-49835: la casella di controllo [!UICONTROL Use Default Value] non è stata salvata

La patch ACSD-49835 risolve il problema che causa il salvataggio non corretto della casella di controllo [!UICONTROL Use Default Value] a livello di archivio per un attributo a selezione multipla. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29. L’ID della patch è ACSD-49835. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La casella di controllo [!UICONTROL Use Default Value] non viene salvata correttamente a livello di archivio per un attributo a selezione multipla.

<u>Passaggi da riprodurre</u>:

1. Creare un **[!UICONTROL Multiple-select Attribute]** in **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** e aggiungerlo a un set di attributi.
1. Vai a **[!UICONTROL Product]** e salva **[!UICONTROL Values]** in **[!UICONTROL All Store Views (Default Scope)]**.
1. Passare a un **[!UICONTROL Store View Scope]** specifico e salvare il prodotto.
1. Vai a **[!UICONTROL Store View Scope]** e seleziona la casella di controllo **[!UICONTROL Use Default Value]**.

<u>Risultati previsti</u>:

I valori degli attributi a selezione multipla vengono salvati correttamente quando si seleziona la casella di controllo [!UICONTROL Use Default Value] in [!UICONTROL Store View Scope].

<u>Risultati effettivi</u>:

I valori degli attributi a selezione multipla non vengono salvati correttamente quando si seleziona la casella di controllo [!UICONTROL Use Default Value] in [!UICONTROL Store View Scope].

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
