---
title: "ACSD-50814: l’utente amministratore non è in grado di creare la nota di credito"
description: Applica la patch ACSD-50814 per risolvere il problema di Adobe Commerce che impedisce a un utente amministratore di creare una nota di credito.
exl-id: bda374cf-6fb7-479f-8130-213ce3cc553e
feature: Admin Workspace, Orders, Returns
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-50814: l’utente amministratore non è in grado di creare una nota di credito

La patch ACSD-50814 risolve il problema che impediva all&#39;utente amministratore di creare una nota di credito. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30. L’ID della patch è ACSD-50814. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Un utente amministratore non è in grado di creare una nota di credito.

<u>Passaggi da riprodurre</u>:

1. Nell’amministrazione di Adobe Commerce, passa a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Shipping methods]** > **[!UICONTROL Free shipping]** e imposta **[!UICONTROL Enable free shipping]** a *[!UICONTROL Yes]*
1. Vai di nuovo a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Tax]**, espandi le impostazioni di calcolo e imposta:
   * [!UICONTROL Shipping prices] = [!UICONTROL Including tax]
   * [!UICONTROL Enable cross border trade] = [!UICONTROL No]
1. Espandere le impostazioni di visualizzazione del prezzo e impostare [!UICONTROL Display shipping prices] = [!UICONTROL Including tax].
1. Espandi [!UICONTROL Orders], [!UICONTROL Invoices], [!UICONTROL Credit memo] impostazioni di visualizzazione e impostazione [!UICONTROL Display shipping amount] = [!UICONTROL Including tax].
1. Cancella cache.
1. Effettua un ordine sul vetrina.
1. Crea una fattura per l&#39;ordine nell&#39;amministratore.
1. Creare una nota di credito.

<u>Risultati previsti</u>:

Viene creata la nota di credito.

<u>Risultati effettivi</u>:

Viene generato il seguente errore:

*Impossibile visualizzare la pagina a causa dell’errore*

```
report.CRITICAL: DivisionByZeroError: Division by zero in vendor/magento/module-sales/Model/Order/Creditmemo/Total/Tax.php:139*
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
