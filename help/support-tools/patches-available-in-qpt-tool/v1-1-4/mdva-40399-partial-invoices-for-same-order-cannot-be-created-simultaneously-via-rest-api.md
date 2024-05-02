---
title: "MDVA-40399: impossibile creare contemporaneamente fatture parziali per lo stesso ordine tramite API"
description: La patch MDVA-40399 risolve il problema che impedisce la creazione simultanea di fatture parziali per lo stesso ordine tramite l'API REST. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4. L'ID della patch è MDVA-40399. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
exl-id: 2444ba57-b30b-4fdf-9e5d-988cf7fa8dd1
feature: REST, Invoices, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# MDVA-40399: impossibile creare contemporaneamente fatture parziali per lo stesso ordine tramite API

La patch MDVA-40399 risolve il problema che impedisce la creazione simultanea di fatture parziali per lo stesso ordine tramite l&#39;API REST. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4. L&#39;ID della patch è MDVA-40399. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Non è possibile creare contemporaneamente fatture parziali per gli stessi ordini utilizzando l&#39;API REST.

<u>Prerequisiti</u>:

Un prodotto configurabile con almeno due varianti.

<u>Passaggi da riprodurre</u>:

1. Aggiungi al carrello entrambe le varianti del prodotto configurabile.
1. Effettua l’ordine.
1. Creare due fatture contemporaneamente per l&#39;ordine tramite l&#39;API Rest.

<u>Risultati previsti</u>:

* Entrambe le fatture devono essere create correttamente.
* `qty_invoiced` deve essere aggiornato per entrambe le fatture nella `sales_order_item` tabella.
* Entrambi i prodotti devono avere una quantità fatturata.

<u>Risultati effettivi</u>:

* Entrambe le fatture sono state create correttamente.
* `qty_invoiced` non viene aggiornato in base a una delle fatture incluse in `sales_order_item` tabella.
* In Admin’s **Vista ordine** pagina, la quantità delle fatture viene visualizzata solo per un prodotto.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento al [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sezione.
