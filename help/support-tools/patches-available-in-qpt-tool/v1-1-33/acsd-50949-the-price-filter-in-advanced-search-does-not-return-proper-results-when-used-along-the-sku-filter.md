---
title: "ACSD-50949: il filtro del prezzo nella ricerca avanzata non restituisce risultati corretti se utilizzato insieme al filtro SKU"
description: Applica la patch ACSD-50949 per risolvere il problema di Adobe Commerce, in cui il filtro del prezzo nella ricerca avanzata non restituisce risultati corretti se utilizzato insieme al filtro SKU.
feature: Orders, Search
role: Admin
exl-id: 3e1f88dc-07f6-4e10-b4b7-163648076cbc
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 1%

---

# ACSD-50949: il filtro del prezzo nella ricerca avanzata non restituisce risultati corretti se utilizzato con il filtro SKU

La patch ACSD-50949 risolve il problema se il filtro del prezzo nella ricerca avanzata non restituisce risultati corretti quando viene utilizzato insieme al filtro SKU. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33. L’ID della patch è ACSD-50949. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it>). Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Problema

Il filtro del prezzo nella ricerca avanzata non restituisce risultati corretti se utilizzato insieme al filtro SKU.

<u>Passaggi da riprodurre</u>:

1. Crea diversi prodotti, ad esempio:

   | SKU | Nome | Prezzo | Quantità |
   |-----|-----------|-------|----------|
   | MJ1 | Prodotto 1 | $ 10 | 10 |
   | MJ2 | Prodotto 2 | $ 15 | 10 |
   | MJ3 | Prodotto 3 | $ 21 | 10 |
   | MJ4 | Prodotto 4 | $ 32 | 10 |
   | MJ5 | Prodotto 5 | $ 33 | 10 |
   | MJ6 | Prodotto 6 | $ 34 | 10 |
   | MJ7 | Prodotto 7 | $ 44 | 10 |

1. Apri **[!UICONTROL Advanced Search]** nella vetrina e cerca per SKU: &quot;MJ&quot;.
1. Fare clic sul collegamento **[!UICONTROL Modify your search]**.
1. Aggiungere un intervallo di prezzi ai criteri da *1* a *21* e fare clic sul pulsante **[!UICONTROL Search]**.

<u>Risultati previsti</u>:

Vengono restituiti solo i prodotti con prezzi compresi nell&#39;intervallo definito.

<u>Risultati effettivi</u>:

Vengono restituiti prodotti con prezzi superiori a *$21*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it>) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it>) nella guida di [!DNL Quality Patches Tool].
