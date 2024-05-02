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

La patch ACSD-52929 risolve il problema della ridondanza delle richieste di reindicizzazione degli elementi di origine predefiniti quando l’indicizzatore di inventario è configurato in modalità asincrona. Questa patch è disponibile quando [!DNL Quality Patches Tool (QPT)] 1.1.38. L’ID della patch è ACSD-52929. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando l’indicizzatore inventario è configurato in modalità asincrona, vi è una ridondanza di richieste per reindicizzare gli articoli di origine predefiniti.

<u>Passaggi da riprodurre</u>:

1. Configura [!DNL RabbitMQ].
1. Abilita la strategia di reindicizzazione asincrona andando su **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Inventory Indexer Setting]** e imposta **[!UICONTROL Stock/Source reindex strategy]=[!UICONTROL Asynchronous]**.
1. Crea un’origine inventario personalizzata.
1. Accedi a [!DNL RabbitMQ] e passare alla scheda code.
1. Verifica `inventory.indexer.sourceItem` mettere in coda e assicurarsi che non contenga messaggi.
1. Apri un prodotto semplice dal backend e aggiungi *[!UICONTROL stock only]* nell’origine personalizzata e salva il prodotto.
1. Carica `inventory.indexer.sourceItem` coda in [!DNL RabbitMQ] e quindi controllare i messaggi.

<u>Risultati previsti</u>:

Nella coda è presente un solo messaggio per l&#39;origine personalizzata.

<u>Risultati effettivi</u>:

Nella coda vengono visualizzati due messaggi: uno per l’origine predefinita e l’altro per l’origine personalizzata.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
