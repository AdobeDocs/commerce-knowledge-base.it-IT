---
title: 'ACSD-47908: *È previsto un valore minore o uguale a 0* errore durante il check-out'
description: Applicare la patch ACSD-47908 per correggere l'errore Adobe Commerce *È previsto un valore minore o uguale a 0* quando si selezionano l'origine e la quantità nella fase di spedizione durante il pagamento.
exl-id: fec90e4b-9cb8-4cd9-9e85-ccada840c896
feature: Admin Workspace, Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# ACSD-47908 *È previsto un valore minore o uguale a 0* errore durante l&#39;estrazione

La patch ACSD-47908 corregge l&#39;errore *È previsto un valore minore o uguale a 0* quando si selezionano l&#39;origine e la quantità nella fase di spedizione durante il pagamento. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27. L’ID della patch è ACSD-47908. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando si selezionano l&#39;origine e la quantità nella fase di spedizione durante il pagamento, viene generato il seguente errore: *È previsto un valore minore o uguale a 0*.

<u>Prerequisiti</u>:

Installa i moduli Adobe Commerce Inventory management (MSI).

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Sources]** e configurare più origini.
1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock]** e creare un nuovo stock.
   * Ora assegna le origini al nuovo stock.
1. Vai a **[!UICONTROL Catalog]** > **[!UICONTROL Products]** e modificare almeno un prodotto.
   * Assicurati che i prodotti siano assegnati alle nuove origini e specifica la quantità disponibile.
1. Vai a **[!UICONTROL Sales]** > **[!UICONTROL Orders]** e creare un nuovo ordine.
1. Aggiungi questi prodotti all’ordine e inseriscili.
1. Clic **[!UICONTROL Ship]**.
1. Selezionare l&#39;origine da cui spedire.
1. Specifica la quantità di ciascun articolo da spedire.
1. Ricarica la pagina.
1. Fai clic su **[!UICONTROL Proceed to Shipment]**.

<u>Risultati previsti</u>:

La nuova pagina di spedizione viene visualizzata senza errori.

<u>Risultati effettivi</u>:

* Impossibile convalidare la quantità immessa.
* Viene generato il seguente errore: *Inserisci un valore minore o uguale a 0*.

  L’errore è, tuttavia, incoerente e potrebbe non apparire sempre.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
