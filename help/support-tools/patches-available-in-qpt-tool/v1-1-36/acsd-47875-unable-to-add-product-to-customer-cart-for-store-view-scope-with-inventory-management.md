---
title: "ACSD-47875: impossibile aggiungere il prodotto al carrello per l’ambito di visualizzazione del negozio con gestione dell’inventario"
description: Applica la patch ACSD-47875 per risolvere il problema di Adobe Commerce che impedisce l’aggiunta di un prodotto al carrello clienti da parte dell’amministratore per un particolare ambito di visualizzazione dello store con gestione dell’inventario.
feature: Inventory, Shopping Cart, Products
role: Admin, Developer
exl-id: fa5ecd65-704f-49bd-b3cc-3d60ff7e1dce
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# ACSD-47875: impossibile aggiungere il prodotto al carrello per l’ambito di visualizzazione del negozio con gestione dell’inventario

La patch ACSD-47875 risolve il problema che impediva l’aggiunta di un prodotto al carrello clienti da parte dell’amministratore per un particolare ambito di visualizzazione dello store con gestione dell’inventario. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.36. L’ID della patch è ACSD-47875. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli utenti amministratori non possono aggiungere un prodotto a un carrello clienti utilizzando la funzionalità **[!UICONTROL Manage Shopping Cart]** in Admin per un determinato ambito di visualizzazione archivio con MSI installato.

<u>Prerequisiti</u>:

[!DNL Adobe Commerce Inventory Management (MSI)] moduli sono installati e abilitati.

<u>Passaggi da riprodurre</u>:

1. Crea un sito web, un negozio e una visualizzazione store.
1. Crea un&#39;origine aggiuntiva diversa da *Predefinita*.
1. Create un nuovo magazzino e assegnatelo al nuovo sito Web e alla nuova sorgente.
1. Crea un nuovo cliente per il nuovo sito web.
1. Assegna un prodotto solo al nuovo sito Web; annulla l’assegnazione dal sito Web predefinito.

   * Assegna la nuova origine e imposta la quantità *superiore a 0* per la nuova origine e *0* per l&#39;origine predefinita.

1. Passare alla pagina **[!UICONTROL Customer Edit]** nell&#39;amministratore. Fare clic su **[!UICONTROL Manage Shopping Cart]**.
1. Modificare l&#39;ambito della visualizzazione archivio nella nuova visualizzazione archivio.
1. Andare alla sezione **[!UICONTROL Products]** e cercare il prodotto.
1. Selezionare il prodotto e fare clic su **[!UICONTROL Add selections to my cart]**.

<u>Risultati previsti</u>:

Il prodotto viene aggiunto al carrello.

<u>Risultati effettivi</u>:

* Viene generato il seguente errore: *Il prodotto che si sta tentando di aggiungere non è disponibile.*
* Il prodotto non viene aggiunto al carrello.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
