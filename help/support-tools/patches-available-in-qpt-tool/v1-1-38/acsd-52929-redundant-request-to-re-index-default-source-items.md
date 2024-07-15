---
title: "ACSD-52929: richiesta ridondante per reindicizzare gli elementi sorgente predefiniti"
description: Applica la patch ACSD-52929 per risolvere il problema di Adobe Commerce in presenza di una richiesta ridondante di reindicizzazione degli elementi di origine predefiniti quando l’indicizzatore inventario è configurato in modalità asincrona.
feature: Configuration, Inventory
role: Admin, Developer
exl-id: 978fe0d0-3917-4ba2-94bb-01c607a825cc
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-52929: richiesta ridondante per reindicizzare gli elementi di origine predefiniti

La patch ACSD-52929 risolve il problema della ridondanza delle richieste di reindicizzazione degli elementi di origine predefiniti quando l’indicizzatore di inventario è configurato in modalità asincrona. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.38. L’ID della patch è ACSD-52929. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando l’indicizzatore inventario è configurato in modalità asincrona, vi è una ridondanza di richieste per reindicizzare gli articoli di origine predefiniti.

<u>Passaggi da riprodurre</u>:

1. Configura [!DNL RabbitMQ].
1. Abilitare la strategia di reindicizzazione asincrona scegliendo **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Inventory Indexer Setting]** e impostando **[!UICONTROL Stock/Source reindex strategy]=[!UICONTROL Asynchronous]**.
1. Crea un’origine inventario personalizzata.
1. Accedere al dashboard [!DNL RabbitMQ] e passare alla scheda code.
1. Controllare la coda di `inventory.indexer.sourceItem` e assicurarsi che non contenga messaggi.
1. Aprire un prodotto semplice dal backend e aggiungere *[!UICONTROL stock only]* all&#39;origine personalizzata e salvare il prodotto.
1. Caricare la coda `inventory.indexer.sourceItem` nel dashboard [!DNL RabbitMQ] e quindi controllare i messaggi.

<u>Risultati previsti</u>:

Nella coda è presente un solo messaggio per l&#39;origine personalizzata.

<u>Risultati effettivi</u>:

Nella coda vengono visualizzati due messaggi: uno per l’origine predefinita e l’altro per l’origine personalizzata.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
