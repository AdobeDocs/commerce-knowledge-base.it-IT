---
title: "ACSD-58163: [!UICONTROL Cart Price Rule] non applica lo sconto dal carrello [!UICONTROL Customer Segment] corrispondente senza codice coupon"
description: Applica la patch ACSD-58163 per risolvere il problema di Adobe Commerce per cui [!UICONTROL Cart Price Rule] non applica uno sconto per un ospite dal carrello [!UICONTROL Customer Segment] corrispondente senza un codice coupon.
feature: Products
role: Admin, Developer
source-git-commit: 7603a482953dc0ac0784ab6e6d3b22e4245e3e75
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---


# ACSD-58163: [!UICONTROL Cart Price Rule] non applica lo sconto dal carrello [!UICONTROL Customer Segment] corrispondente senza codice coupon

La patch ACSD-58163 risolve il problema per cui [!UICONTROL Cart Price Rule] non applica uno sconto dal carrello [!UICONTROL Customer Segment] corrispondente senza un codice coupon. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49. L’ID della patch è ACSD-58163. Il problema è pianificato per essere risolto in Adobe Commerce 2.5.0.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

[!UICONTROL Cart Price Rule] non applica uno sconto per un ospite dal carrello [!UICONTROL Customer Segment] corrispondente senza un codice coupon.

<u>Passaggi da riprodurre</u>:

1. Crea segmento cliente:
   * Per i visitatori.
   * Con la condizione di avere un prodotto nel carrello.

1. Crea *[!UICONTROL Cart Price Rule]*:
   * Senza codice coupon.
   * Con la condizione da abbinare al segmento del cliente visitatore.

1. Crea un prodotto semplice.
1. Apri la vetrina come ospite.
1. Aggiungi un prodotto semplice al carrello.
1. Vai al carrello.

<u>Risultati previsti</u>:

Sconto *[!UICONTROL Cart Price Rule]* applicato.

<u>Risultati effettivi</u>:

Sconto *[!UICONTROL Cart Price Rule]* non applicato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
