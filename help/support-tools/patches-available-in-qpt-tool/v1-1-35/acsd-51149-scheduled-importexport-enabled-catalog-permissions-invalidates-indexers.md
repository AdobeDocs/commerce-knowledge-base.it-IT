---
title: 'ACSD-51149: [!UICONTROL ImportExport] pianificato con [!UICONTROL Catalog Permissions] abilitato invalida gli indicizzatori'
description: Applica la patch ACSD-51149 per risolvere il problema di prestazioni di Adobe Commerce, in cui [!UICONTROL ImportExport] pianificato con [!UICONTROL Catalog Permissions] abilitato invalida gli indicizzatori.
feature: Cache, Data Import/Export
role: Admin
exl-id: 3a26f4be-8e52-407d-bb25-2841458f3aa5
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-51149: [!UICONTROL ImportExport] pianificato con [!UICONTROL Catalog Permissions] abilitato invalida gli indicizzatori

La patch ACSD-51149 risolve il problema per cui [!UICONTROL ImportExport] pianificato con [!UICONTROL Catalog Permissions] abilitato invalida gli indicizzatori. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.35. L’ID della patch è ACSD-51149. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

[!UICONTROL ImportExport] pianificato con [!UICONTROL Catalog Permissions] abilitato invalida gli indicizzatori.

<u>Passaggi da riprodurre</u>:

1. Abilita *[!UICONTROL Catalog Permissions]*.
1. Imposta tutti gli indici su *[!UICONTROL Update by Schedule]*.
1. Crea un prodotto semplice.
1. Esporta questo prodotto tramite **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]**.
1. Scarica il file CSV esportato e inseriscilo in `<AC root folder>/var/import`.
1. Crea un’importazione di prodotti pianificata con il file CSV scaricato.
1. Esegui reindicizzazione completa.
1. Controlla lo stato degli indicizzatori. Tutti gli indici devono essere nello stato *[!UICONTROL Ready]*.
1. Esegui l’importazione pianificata creata dalla griglia.
1. Ricontrolla lo stato degli indicizzatori.

<u>Risultati previsti</u>:

Tutti gli indici sono nello stato *[!UICONTROL Ready]*.

<u>Risultati effettivi</u>:

Alcuni indicizzatori sono nello stato *[!UICONTROL Reindex Required]*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
