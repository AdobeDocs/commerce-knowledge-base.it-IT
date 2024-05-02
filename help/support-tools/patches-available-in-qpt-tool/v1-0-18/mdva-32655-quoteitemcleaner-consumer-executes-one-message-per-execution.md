---
title: 'MDVA-32655: il consumer "quoteItemCleaner" esegue un messaggio per esecuzione'
description: La patch MDVA-32655 corregge lo stato errato del messaggio "in corso" sul messaggio "completo" corretto per il consumer "quoteItemCleaner" dopo l’eliminazione di diversi prodotti. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18. L’ID della patch è 32655. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.3.
exl-id: 07213430-f779-4a53-89fd-bc3905e13675
feature: Quotes
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-32655: il consumer &quot;quoteItemCleaner&quot; esegue un messaggio per esecuzione

La patch MDVA-32655 corregge lo stato errato del messaggio &quot;in corso&quot; con il messaggio &quot;completo&quot; corretto per il consumatore `quoteItemCleaner` dopo aver eliminato diversi prodotti. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18. L’ID della patch è 32655. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.3.3

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud e Adobe Commerce on-premise 2.3.0 - 2.4.2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il `quoteItemCleaner` il consumer esegue un solo messaggio a ogni esecuzione.

<u>Passaggi da riprodurre</u>:

1. Controlla la `queue_message_status` e assicurati che tutti i messaggi della coda esistenti siano in stato &quot;Completato&quot; (ID stato 4).
1. Interrompi l’esecuzione automatica del cron di Adobe Commerce.
1. Crea due o tre prodotti semplici.
1. Effettuare una cancellazione di massa su questi tre prodotti semplici.
1. In `queue_message_status` tabella sono presenti tre nuovi record per `catalog_product_removed_queue` argomento con ID stato 2 (nuovo record).
1. Esegui il comando seguente per elaborare questi elementi in sospeso `catalog_product_removed_queue` messaggi:

   ```bash
   bin/magento queue:consumers:start quoteItemCleaner --single-thread --max-messages=100
   ```

<u>Risultati previsti</u>:

```sql
select * from queue_message_status s join queue q on s.queue_id = q.id where q.name = "catalog_product_removed_queue";
```

Tutte le `catalog_product_removed_queue` gli stati dei messaggi vengono aggiornati al completamento (ID=4).

<u>Risultati effettivi</u>:

Solo un record dei tre viene aggiornato allo stato &quot;Completato&quot; (ID = 4). Lo stato degli altri due messaggi è ID stato = 3 (in corso). Viene generato un backlog con messaggi di coda non elaborati.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento al [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
