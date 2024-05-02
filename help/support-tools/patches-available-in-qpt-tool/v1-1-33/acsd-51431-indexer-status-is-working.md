---
title: '"ACSD-51431: lo stato dell’indicizzatore è *[!UICONTROL Working]* anche se non sono presenti voci nel changelog'''
description: Applica la patch ACSD-51431 per risolvere il problema Adobe Commerce relativo allo stato dell’indicizzatore*[!UICONTROL Working]* anche se non sono presenti voci nel changelog.
feature: Logs, Price Indexer
role: Admin
exl-id: 85977b78-7f6b-47c7-b33e-16668bdf98fe
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACSD-51431: lo stato dell&#39;indicizzatore è *[!UICONTROL Working]* anche se non sono presenti voci nel changelog

La patch ACSD-51431 risolve il problema di prestazioni in cui lo stato dell&#39;indicizzatore è *[!UICONTROL Working]* anche se non sono presenti voci nel changelog. Questa patch è disponibile quando [!DNL Quality Patches Tool (QPT)] 1.1.33. L’ID della patch è ACSD-51431. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Lo stato dell’indicizzatore è *[!UICONTROL Working]* anche se non sono presenti voci nel changelog.

<u>Passaggi da riprodurre</u>:

1. Imposta **[!UICONTROL indexers]** a [!UICONTROL Update on Schedule].
1. Configura il processo cron in modo che venga eseguito ogni minuto.
1. Salva le modifiche apportate a prodotti diversi simultaneamente.
1. Esegui `bin/magento indexer:status` tra un paio di minuti.

<u>Risultati previsti</u>:

Le modifiche vengono elaborate e gli indicizzatori sono in *[!UICONTROL Ready]* stato. Il *[!UICONTROL Schedule]* lo stato è *[!UICONTROL idle (0 in the backlog)]*.

<u>Risultati effettivi</u>:

Le modifiche vengono elaborate e gli indicizzatori sono in *[!UICONTROL Ready]* stato. Tuttavia, il *[!UICONTROL Schedule]* visualizzazioni dello stato *[!UICONTROL working (0 in the backlog)]*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
