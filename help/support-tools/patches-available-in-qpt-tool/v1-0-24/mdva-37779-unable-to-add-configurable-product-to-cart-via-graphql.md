---
title: "MDVA-37779: impossibile aggiungere un prodotto configurabile al carrello tramite GraphQL"
description: La patch di MDVA-37779 Adobe Commerce risolve il problema dell'impossibilità di aggiungere al carrello un prodotto configurabile quando l'ID del sito Web non è uguale all'ID dello store. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24. L'ID della patch è MDVA-37779. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4. 
exl-id: 5f344896-39c3-4e17-89b8-1b987bae2968
feature: GraphQL, Configuration, Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# MDVA-37779: impossibile aggiungere un prodotto configurabile al carrello tramite GraphQL

La patch di MDVA-37779 Adobe Commerce risolve il problema dell&#39;impossibilità di aggiungere al carrello un prodotto configurabile quando l&#39;ID del sito Web non è uguale all&#39;ID dello store. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24. L&#39;ID della patch è MDVA-37779. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce on-premise e Adobe Commerce sull’infrastruttura cloud 2.4.2 - 2.4.2-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Non è possibile aggiungere al carrello un prodotto configurabile se l’ID del sito web non è uguale all’ID del negozio.

<u>Prerequisiti</u>:

Avere una seconda visualizzazione del sito Web, store e store in cui l&#39;ID del sito Web non è uguale all&#39;ID store.

<u>Passaggi da riprodurre</u>:

1. Creare un carrello vuoto utilizzando la mutazione GraphQl `createEmptyCart`.
1. Prova ad aggiungere al carrello un prodotto configurabile utilizzando `addConfigurableProductsToCart` mutazione.

<u>Risultati previsti</u>:

Prodotto aggiunto al carrello.

<u>Risultati effettivi</u>:

Viene visualizzato un errore: *Impossibile aggiungere il prodotto con SKU xxxx al carrello: impossibile trovare il sito Web con ID 3 richiesto. Verifica il sito web e riprova.*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.


## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili nello strumento QPT, consultare [Patch disponibili nello strumento QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sezione.
