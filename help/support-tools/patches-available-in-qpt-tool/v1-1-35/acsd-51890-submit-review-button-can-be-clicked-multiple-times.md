---
title: "ACSD-51890: è possibile fare clic più volte sul pulsante [!UICONTROL Submit review]"
description: Applica la patch ACSD-51890 per risolvere il problema Adobe Commerce, in cui è possibile fare clic più volte sul pulsante [!UICONTROL Submit Review] senza [!DNL Google reCAPTCHA v3] convalida.
feature: Products
role: Admin
exl-id: f6369a24-24bd-4e5e-a870-a13f507ada94
source-git-commit: 7dbf9a796fe2026b0657b719d10e5bb21b964fb6
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-51890: è possibile fare clic più volte sul pulsante **[!UICONTROL Submit Review]** senza convalida **[!DNL Google reCAPTCHA v3]**

>[!NOTE]
>
>Questa patch è sostituita da [ACSD-55112](/help/support-tools/patches-available-in-qpt-tool/v1-1-42/acsd-55112-submit-review-button-can-be-clicked-multiple-times.md).

La patch ACSD-51890 risolve il problema per cui è possibile fare clic più volte sul pulsante **[!UICONTROL Submit Review]** senza la convalida **[!DNL Google reCAPTCHA v3]**. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.35. L’ID della patch è ACSD-51890. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

È possibile fare clic più volte sul pulsante **[!UICONTROL Submit Review]** senza la convalida **[!DNL Google reCAPTCHA v3]**.

<u>Passaggi da riprodurre</u>:

1. Abilita **[!DNL Google reCAPTCHA v3]** per la revisione del prodotto.
1. Aprire la pagina del prodotto, passare alla sezione **[!UICONTROL Review]** e assicurarsi che [!DNL reCAPTCHA] sia visibile.
1. Compila il modulo di revisione e fai clic più volte sul pulsante **[!UICONTROL Submit Review]**.
1. Apri la sezione **[!UICONTROL Review]** dall&#39;amministratore.

<u>Risultati previsti</u>

Le revisioni duplicate non vengono create.

<u>Risultati effettivi</u>

Vengono create revisioni duplicate.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) nella guida di [!DNL Quality Patches Tool].
