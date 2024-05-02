---
title: 'MDVA-43601: i trigger vengono rimossi dalla tabella "catalogrule_product_price" dopo la reindicizzazione completa'
description: La patch MDVA-43601 risolve il problema in cui i trigger vengono rimossi dalla tabella "catalogrule_product_price" dopo una reindicizzazione completa di "catalogrule_rule" o "catalogrule_product". Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13. L'ID della patch è MDVA-43601. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
exl-id: fdef1e56-79ec-455a-8a29-b82f1c8ceea7
feature: Catalog Management, Orders, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# MDVA-43601: i trigger vengono rimossi dalla tabella &quot;catalogrule_product_price&quot; dopo la reindicizzazione completa

La patch MDVA-43601 risolve il problema della rimozione dei trigger da `catalogrule_product_price` dopo una reindicizzazione completa di `catalogrule_rule` o `catalogrule_product`. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13. L&#39;ID della patch è MDVA-43601. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli attivatori vengono rimossi da `catalogrule_product_price` dopo una reindicizzazione completa di `catalogrule_rule` o `catalogrule_product`.

<u>Passaggi da riprodurre</u>:

1. Imposta tutti gli indici su *Aggiorna per pianificazione*.
1. Controlla i trigger creati per `catalogrule_product_price` eseguendo la seguente richiesta SQL:

   ```sql
   show triggers like '%catalogrule_%'\G
   ```

1. Reindicizzazione manuale `catalogrule_rule` o `catalogrule_product` eseguendo il comando seguente: `bin/magento indexer:reindex catalogrule_rule`
1. Controlla i trigger di `catalogrule_product_price` tabella.

<u>Risultati previsti</u>:

Triggers in `catalogrule_product_price` vengono mantenute dopo una reindicizzazione completa.

<u>Risultati effettivi</u>:

Nessun trigger trovato per `catalogrule_product_price` tabella.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
