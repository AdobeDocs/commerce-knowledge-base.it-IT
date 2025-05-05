---
title: "ACSD-47004: IVA non applicata all’indirizzo di fatturazione senza partita IVA"
description: Applica la patch ACSD-47004 per risolvere il problema Adobe Commerce in cui l’IVA non viene applicata a un indirizzo di fatturazione senza un ID IVA.
exl-id: 04706219-be1d-4d9a-a8bf-f5c24b45076d
feature: Customer Service, Shipping/Delivery, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 1%

---

# ACSD-47004: IVA non applicata all&#39;indirizzo di fatturazione senza ID IVA

La patch ACSD-47004 risolve il problema in cui l’IVA non viene applicata a un indirizzo di fatturazione senza un ID IVA. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24. L’ID della patch è ACSD-47004. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;IVA non viene applicata a un indirizzo di fatturazione senza un ID IVA.

<u>Passaggi da riprodurre</u>:

1. Apri [!UICONTROL Commerce Admin] > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Create New Account Options]** e imposta **[!UICONTROL Enable Automatic Assignment to Customer Group]** su *[!UICONTROL Yes]*.
1. Imposta gruppi diversi per le convalide ID IVA. Ad esempio:
   ![Convalide ID-IVA](/help/support-tools/patches-available-in-qpt-tool/assets/vat-id-validations.png)
1. Registra un nuovo cliente.
1. Aggiungi un nuovo indirizzo predefinito senza IVA. Ad esempio:

   ```
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   ```

1. Verificare che il gruppo del cliente rimanga [!UICONTROL General].
1. Modifica questo indirizzo e aggiungi un numero di partita IVA valido:

   ```
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   VAT: DE329376919
   ```

1. Assicurarsi che il gruppo del cliente sia cambiato in [!UICONTROL Retailer].
1. Modifica l&#39;indirizzo e rimuovi il numero di partita IVA:

   ```
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   ```

<u>Risultati previsti</u>:

Il gruppo di clienti viene modificato automaticamente nel gruppo predefinito [!UICONTROL General].

<u>Risultati effettivi</u>:

Il gruppo di clienti non viene modificato automaticamente nel gruppo predefinito [!UICONTROL General].

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
