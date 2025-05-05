---
title: "ACSD-50621: i prezzi di livello per i diversi siti web nel catalogo condiviso non sono visibili"
description: Applica la patch ACSD-50621 per risolvere il problema di Adobe Commerce, in cui i prezzi dei diversi siti web nel catalogo condiviso non sono visibili quando vengono modificati in un ambiente con più siti web.
exl-id: 6d6635bc-4f76-4e2f-9bc7-0276cced8ca9
feature: Catalog Management, Orders
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# ACSD-50621: i prezzi di livello per i diversi siti web nel catalogo condiviso non sono visibili

La patch ACSD-50621 risolve il problema che non è possibile visualizzare i prezzi dei diversi siti Web nel catalogo condiviso in un ambiente con più siti Web. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.32. L’ID della patch è ACSD-50621. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I prezzi di livello per i diversi siti web nel catalogo condiviso non sono visibili quando li si modifica in un ambiente multi-sito.

<u>Passaggi da riprodurre</u>:

1. Imposta **[!UICONTROL Catalog Price Scope]** su **[!UICONTROL Website]**.
1. Crea un altro sito Web, store e storeview.
1. Crea un prodotto semplice e assegnalo a tutti i siti web.
1. Crea un catalogo condiviso personalizzato.
1. Passare a **[!UICONTROL Set Pricing and Structure]** per il catalogo condiviso personalizzato creato.
1. Nel passaggio 1: selezionare i prodotti per il catalogo. Aggiungi il prodotto semplice creato.
1. Nel passaggio 2: impostare i prezzi personalizzati e fare clic su **[!UICONTROL Configure]**.
1. Impostare prezzi di livello diversi per siti Web diversi.
1. Selezionare **[!UICONTROL Done]**, fare clic su **[!UICONTROL Generate Catalog]** e quindi su **[!UICONTROL Save]**.
1. Esegui cron.
1. Passa a **[!UICONTROL Set Pricing and Structure]** > **[!UICONTROL Configure]** > **[!UICONTROL Next]** > **[!UICONTROL Configure]** e verifica il prezzo del livello.

<u>Risultati previsti</u>:

Sono presenti tutti i prezzi di livello configurati in precedenza per i diversi siti Web.

<u>Risultati effettivi</u>:

I prezzi di livello configurati in precedenza non sono presenti.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
