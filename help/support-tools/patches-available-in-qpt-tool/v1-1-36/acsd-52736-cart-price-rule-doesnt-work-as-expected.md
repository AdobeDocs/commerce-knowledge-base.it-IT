---
title: 'ACSD-52736: [!UICONTROL Cart Price Rule] non funziona come previsto'
description: Applicare la patch ACSD-52736 per risolvere il problema di Adobe Commerce in cui un [!UICONTROL Cart Price Rule] che include i requisiti per la quantità di prodotto configurabile non funziona come previsto.
feature: Shopping Cart, Products
role: Admin, Developer
exl-id: 8403b418-b197-4695-88a8-e322b18cd4ad
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-52736: [!UICONTROL Cart Price Rule] non funziona come previsto

La patch ACSD-52736 risolve il problema che causa il mancato funzionamento di [!UICONTROL Cart Price Rule] che include i requisiti per la quantità di prodotto configurabile. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.36. L’ID della patch è ACSD-52736. Il problema è stato risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Un [!UICONTROL Cart Price Rule] che include i requisiti per la quantità di prodotto configurabile non funziona come previsto.

<u>Passaggi da riprodurre</u>:

1. Crea una regola carrello:
   * [!UICONTROL Apply] = percentuale di sconto sul prezzo del prodotto
   * [!UICONTROL Discount Amount] = 60
   * [!UICONTROL Maximum Qty Discount is Applied to] = 1
   * [!UICONTROL Discount Qty Step (Buy X)] = 1
   * Applica la regola solo agli articoli del carrello che soddisfano le seguenti condizioni: La quantità nel carrello è 1
2. Aggiungi al carrello un prodotto con [!UICONTROL Qty] = 2.
3. Controlla i prezzi del carrello.

<u>Risultati previsti</u>:

La regola non viene applicata perché la quantità dei prodotti nel carrello è *2*.

<u>Risultati effettivi</u>:

Viene applicato lo sconto.

<u> Passaggi aggiuntivi richiesti dopo l&#39;installazione della patch</u>:

Dopo aver applicato la patch, è necessario rimuovere e aggiungere nuovamente le condizioni della regola del carrello che utilizzano l&#39;attributo *Quantità*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
