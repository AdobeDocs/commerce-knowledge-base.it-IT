---
title: 'ACSD-51408: lo stato dell''elemento dell''ordine non è impostato correttamente su [!UICONTROL backordered]'
description: Applicare la patch ACSD-51408 per risolvere il problema Adobe Commerce in cui lo stato dell'elemento dell'ordine non è impostato correttamente su [!UICONTROL backordered].
feature: B2B, Orders
role: Admin
exl-id: 0355beca-4612-438f-8f91-be42d8d637e9
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# ACSD-51408: lo stato dell&#39;elemento dell&#39;ordine non è impostato correttamente su *[!UICONTROL backordered]*

La patch ACSD-51408 risolve il problema relativo all&#39;impostazione errata dello stato dell&#39;elemento dell&#39;ordine su [!UICONTROL backordered]. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.33. L’ID della patch è ACSD-51408. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Lo stato dell&#39;elemento dell&#39;ordine non è impostato correttamente su *[!UICONTROL backordered]*.

<u>Prerequisiti</u>:

Sono installati i moduli Adobe Commerce B2B e Inventory management (MSI).

<u>Passaggi da riprodurre</u>:

1. Crea un nuovo sito Web, store e visualizzazione store.
1. Crea una nuova origine.
1. Create un nuovo materiale collegato al nuovo sito Web creato nel passaggio 1 e assegnate l&#39;origine creata nel passaggio 2.
1. Crea una società e assegnala al nuovo sito Web creato nel passaggio 1.
1. Creare un nuovo cliente e assegnarlo all&#39;azienda creata nel passaggio 4.
1. Creare un prodotto, assegnarlo al nuovo sito Web e impostare **[!UICONTROL default stock]** = *0* e **[!UICONTROL new stock]** su un valore maggiore di *0*.
1. Abilita **[!UICONTROL backorders]**.
1. Abilita il metodo di pagamento **[!UICONTROL Check/Money Order]** per il nuovo ambito del sito Web.
1. Abilita **[!UICONTROL Flat Rate shipping method]** per il nuovo ambito del sito Web.
1. Crea un nuovo ordine da **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Create New Order]**.
1. Selezionare il nuovo cliente creato al punto 5.
1. Selezionare il nuovo archivio creato al punto 1.
1. Scegliere il prodotto creato al punto 6.
1. Compila le informazioni dell’ordine, inclusi i metodi di pagamento e di spedizione.
1. Invia l’ordine.
1. Controlla lo *stato elemento*.

<u>Risultati previsti</u>

L&#39;articolo è disponibile per la spedizione dal magazzino. Lo stato dell&#39;elemento è *[!UICONTROL ordered]*.

<u>Risultati effettivi</u>

Lo stato dell&#39;elemento è *[!UICONTROL backordered]*.

>[!MORELIKETHIS]
>
>[Lo stato dell&#39;articolo dell&#39;ordine non è impostato correttamente su *[!UICONTROL Ordered]* quando le scorte di prodotto sono 0.](/help/support-tools/patches-available-in-qpt-tool/v1-1-33/acsd-51735-order-item-status-incorrectly-set.md)

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
