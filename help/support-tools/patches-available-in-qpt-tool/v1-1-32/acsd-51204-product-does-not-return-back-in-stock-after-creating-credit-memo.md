---
title: "ACSD-51204: il prodotto non torna in magazzino dopo la creazione della nota di credito"
description: Applicare la patch ACSD-51204 per risolvere il problema di Adobe Commerce, in cui il prodotto non ritorna in magazzino dopo la creazione della nota di credito.
feature: Orders, Products, Returns
role: Admin
exl-id: 302033bc-2ca5-40d6-b692-24ae46b21c31
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# ACSD-51204: il prodotto non torna in magazzino dopo la creazione della nota di credito

La patch ACSD-51204 risolve il problema che impedisce al prodotto di tornare a magazzino dopo la creazione della nota di credito. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.32. L’ID della patch è ACSD-51204. Il problema è stato risolto in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il prodotto esaurito non ritorna in magazzino dopo la creazione della nota di credito.

<u>Passaggi da riprodurre</u>:

1. Installa **[!UICONTROL Adobe Commerce]** e abilita **[!UICONTROL Inventory Management Module]** con impostazione predefinita *sorgente* e *stock* solo.
1. Aggiungi un **[!UICONTROL new product]** con una quantità di *10*.
1. Assegna il prodotto a **[!UICONTROL default stock]**.
1. Nella vetrina, aggiungi il prodotto al carrello e ordina per una quantità intera disponibile pari a 10.
1. Nel pannello di amministrazione, genera un’ *fattura* e *spedizione* per l’ordine.
1. Creare un **[!UICONTROL Credit Memo]** con *ritorno a magazzino* casella di controllo selezionata per tutti gli elementi.
1. Controlla i **[!UICONTROL Salable Quantity]** in Admin.

<u>Risultati previsti</u>:

La quantità vendibile del prodotto deve essere restituita a *10*.

<u>Risultati effettivi</u>:

La quantità vendibile del prodotto viene lasciata come *0*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) nel [!DNL Quality Patches Tool] guida.
