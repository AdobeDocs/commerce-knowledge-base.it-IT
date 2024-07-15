---
title: 'patch MDVA-33344: ID del set di attributi "rma-item" codificato a livello hardware'
description: La patch MDVA-33344 risolve il problema relativo all'utilizzo dell'ID del set di attributi predefinito dell'entità "rma\_item" codificato a livello rigido invece del valore del database. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16. Il problema è stato risolto o è pianificato per essere risolto in Adobe Commerce 2.4.3.
exl-id: 2ef894a3-eea0-4f9f-8d26-984cd408458c
feature: Attributes, B2B
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# patch MDVA-33344: ID del set di attributi &quot;rma-item&quot; hardcoded

La patch MDVA-33344 risolve il problema relativo all&#39;utilizzo dell&#39;ID del set di attributi predefinito dell&#39;entità &quot;rma\_item&quot; codificato a livello rigido invece del valore del database. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16. Il problema è stato risolto o è pianificato per essere risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch è stata creata per Adobe Commerce versione:** Adobe Commerce sull&#39;infrastruttura cloud 2.3.4

**Compatibile con le versioni di Adobe Commerce:** Adobe Commerce su infrastruttura cloud e Adobe Commerce on-premise 2.3.0 - 2.4.2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;endpoint WebAPI `/rest/default/V1/returnsAttributeMetadata` restituisce un risultato vuoto se l&#39;ID del set di attributi predefinito dell&#39;entità &quot;rma\_item&quot; è diverso dall&#39;ID di installazione predefinito.

<u>Passaggi da riprodurre</u>:

Effettuare una chiamata API a `/rest/default/V1/returnsAttributeMetadata`.

<u>Risultato previsto</u>:

I dati vengono restituiti.

<u>Risultato effettivo</u>:

Viene restituito un risultato vuoto.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta le [patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
