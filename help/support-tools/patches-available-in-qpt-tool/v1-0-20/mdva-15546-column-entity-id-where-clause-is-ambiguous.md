---
title: "MDVA-15546: colonna 'entity_id' dove la clausola è ambigua"
description: "La patch MDVA-15546 risolve problemi di prestazioni che possono essere correlati ad alcune estensioni Amazon. Questo problema in è indicato dal seguente errore nei registri eccezioni: *where* *Column 'entity\\_ id' in where clause is ambiguous, query was: SELECT \\`main\\_table\\`.\\*, \\`extension\\_attribute\\_amazon\\_order\\_reference\\_id* \\`. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20. L’ID della patch è MDVA-15546."
exl-id: d58c1728-eb7a-49e8-a329-3197f2339b9c
feature: B2B, Commerce Intelligence
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# MDVA-15546: colonna &#39;entity_id&#39; in cui la clausola è ambigua

La patch MDVA-15546 risolve problemi di prestazioni che possono essere correlati ad alcune estensioni Amazon. Questo problema in è indicato dal seguente errore nei registri eccezioni: *dove*   *Colonna &quot;entity\_id&quot; in cui la clausola è ambigua. Query: SELECT \`main\_table\`.\*, \`extension\_attribute\_amazon\_order\_reference\_id* \`. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20. L&#39;ID della patch è MDVA-15546.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.2.5

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.3.0 - 2.4.2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Problemi di prestazioni che possono essere correlati ad alcune estensioni Amazon.

<u>Prerequisiti</u>:

Pulisci Adobe Commerce con B2B e Amazon\_Payment.

<u>Passaggi da riprodurre</u>:

1. Vai alla pagina della vetrina.
1. Aggiungi il prodotto al carrello.
1. Attendere o attivare il processo cron `flush_preview_quotas`.

<u>Risultato effettivo</u>:

Quando si seleziona `var/log/exception/log`, viene visualizzato il seguente errore:

*`report.ERROR: Cron Jobflush_preview_quotashas an error: SQLSTATE[23000]: Integrity constraint violation: 1052 Column 'entity_id' in where clause is ambiguous, query was: SELECT `main_table`.*, `extension_attribute_amazon_order_reference_id`.`amazon_order_reference_id` AS `extension_attribute_amazon_order_reference_id_amazon_order_reference_id`, `extension_attribute_amazon_order_reference_id`.`quote_id` AS `extension_attribute_amazon_order_reference_id_quote_id`, `extension_attribute_amazon_order_reference_id`.` sandbox_simulation_reference` AS `extension_attribute_amazon_order_reference_id_sandbox_simulation_reference`, `extension_attribute_amazon_order_reference_id`.`confermato` AS `extension_attribute_amazon_order_reference_id_confirm` FROM `preventivo` AS `main_table` LEFT JOIN `amazon_quote` AS `extension_attribute_amazon_order_reference_id` ON main_table.entity_id = extension_attribute_amazon_order_reference_id.quote_id WHERE ...`*

<u>Risultato previsto</u>:

Processo di correzione completato senza errori.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
