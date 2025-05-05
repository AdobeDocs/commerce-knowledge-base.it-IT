---
title: "ACSD-52143: le opzioni personalizzate vengono rimosse dopo l’importazione del prodotto"
description: Applica la patch ACSD-52143 per risolvere il problema di Adobe Commerce, per cui le opzioni di personalizzazione vengono rimosse dopo l’importazione del prodotto.
feature: Data Import/Export
role: Admin, Developer
exl-id: 7dde1efe-37a3-443f-9ce1-82cf1b3d9da7
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-52143: le opzioni personalizzate vengono rimosse dopo l’importazione del prodotto

La patch ACSD-52143 risolve il problema della rimozione delle opzioni personalizzate dopo l’importazione del prodotto. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.37. L’ID della patch è ACSD-52143. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.6-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le opzioni personalizzate vengono rimosse dopo l’importazione del prodotto.

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL Store]** > **[!UICONTROL All Stores]** e configura un&#39;istanza multi-store (un sito Web con due visualizzazioni store).
1. Vai a **[!UICONTROL Catalog]** > **[!UICONTROL Products]** e crea due prodotti con [!UICONTROL Customizable Options].
1. In ogni prodotto, aggiungere un [!UICONTROL Customizable Option].
1. Passa alla seconda vista store e modifica il nome del prodotto su ciascun prodotto.
1. Vai a **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]** ed esporta i due prodotti creati.
1. Scarica il file CSV.
1. Vai a **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]** e reimporta il file.
1. Controlla entrambi i prodotti.

<u>Risultati previsti</u>:

Le opzioni personalizzate non vengono rimosse dopo l’importazione del prodotto.

<u>Risultati effettivi</u>:

Le opzioni di dogana vengono rimosse dopo l’importazione del prodotto.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
