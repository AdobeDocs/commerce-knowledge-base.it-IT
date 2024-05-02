---
title: '"ACSD-54319: il prezzo del prodotto è pari a zero *[!UICONTROL Products in Carts]* report'''
description: Applica la patch ACSD-54319 per risolvere il problema di Adobe Commerce in cui il prezzo del prodotto mostra zero in *[!UICONTROL Products in Carts]* rapporto
feature: Reporting, Products
role: Admin, Developer
exl-id: f53b3ed3-d5d5-461c-bba2-4f9f3f038580
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# ACSD-54319: il prezzo del prodotto è pari a zero *[!UICONTROL Products in Carts]* rapporto

La patch di ACSD-54319 risolve il problema in cui il prezzo del prodotto è pari a zero *[!UICONTROL Products in Carts]* rapporto. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40. L’ID della patch è ACSD-54319. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.5-p5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il prezzo del prodotto è pari a zero *[!UICONTROL Products in Carts]* rapporto.

<u>Passaggi da riprodurre</u>:

1. Imposta **[!UICONTROL Catalog Price Scope]** a **[!UICONTROL Website]** da **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Price]** > **[!UICONTROL Catalog Price Scope]**.
1. Crea un secondo sito Web da **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**.
1. Creare un prodotto da **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Assegna il prodotto solo al secondo sito Web.
1. Aggiungi un prodotto al carrello dal secondo sito web.
1. Vai a **[!UICONTROL Admin]** > **[!UICONTROL Reports]** > **[!UICONTROL Marketing]** > **[!UICONTROL Products In Carts]** griglia.
1. Controlla la *[!UICONTROL Price]* colonna in *[!UICONTROL Products In Carts]* griglia.

<u>Risultati previsti</u>:

Il prezzo del prodotto non è zero in *[!UICONTROL Products in Carts]* griglia dei rapporti.

<u>Risultati effettivi</u>:

Prezzo del prodotto pari a zero in *[!UICONTROL Products in Carts]* griglia dei rapporti.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
