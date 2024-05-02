---
title: "ACSD-54111: l’immagine della miniatura del prodotto non viene visualizzata"
description: Applica la patch ACSD-54111 per risolvere il problema di Adobe Commerce, per cui tutte le immagini vengono sostituite dall’immagine segnaposto del prodotto predefinita.
feature: Products
role: Admin, Developer
exl-id: 087786e3-9d61-4fef-8884-8d22fa9170e3
source-git-commit: a863015920917050106ed5d210d0511515807cc7
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-54111: l’immagine della miniatura del prodotto non viene visualizzata

La patch ACSD-54111 risolve il problema relativo alla sostituzione di tutte le immagini con l&#39;immagine segnaposto del prodotto predefinita. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.38. L’ID della patch è ACSD-54111. Il problema è stato risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione): 2.4.5-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione): 2.4.2 - 2.4.5-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’immagine della miniatura del prodotto non viene visualizzata.

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL Content]** > **[!UICONTROL Design]** > **[!UICONTROL Configuration]** > **[!UICONTROL Edit Theme]** > **[!UICONTROL Product Image Watermarks]** > **[!UICONTROL Thumbnail]**.
1. Carica l’immagine con una miniatura e imposta la posizione dell’immagine come *[!UICONTROL Center]*.
1. Fai clic su **[!UICONTROL Save Configuration]**.
1. Cancella cache.
1. Vai alla vetrina come ospite/cliente.
1. Aggiungi un prodotto al carrello.
1. Esegui `bin/magento catalog:image:resize` dalla console.
1. Apri il mini-carrello sul front-end o sulla griglia prodotti sul backend per vedere se le miniature delle immagini sono visibili.

<u>Risultati previsti</u>:

Le immagini del prodotto non vengono sostituite con l’immagine segnaposto.

<u>Risultati effettivi</u>:

Le immagini del prodotto vengono sostituite dall’immagine segnaposto del prodotto predefinita.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
