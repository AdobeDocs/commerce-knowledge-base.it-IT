---
title: "ACSD-51238: l’origine dell’inventario viene rimossa quando si aggiorna un prodotto configurabile e si modifica il prezzo"
description: Applicare la patch ACSD-51238 per risolvere il problema di Adobe Commerce in cui l'origine inventario viene rimossa quando si aggiorna un prodotto configurabile e si modifica il prezzo.
exl-id: ab2f60fd-5da3-45f7-a489-6f4f9d34e1f1
feature: Configuration, Inventory, Orders, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-51238: l’origine inventario viene rimossa quando si aggiorna un prodotto configurabile e si modifica il prezzo

La patch ACSD-51238 risolve il problema della rimozione dell&#39;origine inventario quando si aggiorna un prodotto configurabile e si modifica il prezzo. Questa patch è disponibile quando [!DNL Quality Patches Tool (QPT)] 1.1.32. L’ID della patch è ACSD-51238. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’origine dell’inventario viene rimossa quando si aggiorna un prodotto configurabile e si modifica il prezzo.

<u>Passaggi da riprodurre</u>:

1. Installa **[!DNL Adobe Commerce]** con **[!DNL Inventory module]**
1. Vai a **[!UICONTROL Admin]** -> **[!UICONTROL Stores]** -> **[!UICONTROL Inventory]** e creare *due sorgenti* e *due scorte*.
1. Creare un **[!UICONTROL configurable product]** e assegnarlo a **[!UICONTROL default sources]** o **[!UICONTROL newly created sources]**.
1. Fai clic sul pulsante **[!UICONTROL next button]** e *salva* il prodotto.
1. Ora modifica lo stesso **[!UICONTROL Configurable Product]** e fai clic su **[!UICONTROL Edit Configuration]** all&#39;interno del **[!UICONTROL Configuration tab]**.
1. In entrata `Step 3: Bulk Images,Price and Quantity`, modifica il `price` e lasciare `Quantity` e `Images` a `Skip quantity at this time` e `Skip image uploading at this time` rispettivamente.
1. Fai clic su **[!UICONTROL next button]** e generare il prodotto.

<u>Risultati previsti</u>

Quantità per origine all&#39;interno del **[!UICONTROL Configuration tab]** non deve essere vuoto.

<u>Risultati effettivi</u>

Quantità per origine all&#39;interno del **[!UICONTROL Configuration tab]** è vuoto.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) nel [!DNL Quality Patches Tool] guida.
