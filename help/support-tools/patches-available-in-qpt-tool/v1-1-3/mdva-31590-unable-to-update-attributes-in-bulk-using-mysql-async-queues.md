---
title: "MDVA-31590: impossibile aggiornare gli attributi in blocco utilizzando le code asincrone MySQL"
description: La patch MDVA-31590 risolve il problema che impediva agli utenti di aggiornare gli attributi in blocco utilizzando le code asincrone MySQL. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.3. L'ID della patch è MDVA-31590. Il problema è stato risolto in Adobe Commerce 2.4.2.
exl-id: 57db28dd-a739-4a77-927d-6339af4fa4a6
feature: Attributes, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '585'
ht-degree: 0%

---

# MDVA-31590: impossibile aggiornare gli attributi in blocco utilizzando le code asincrone MySQL

La patch MDVA-31590 risolve il problema che impediva agli utenti di aggiornare gli attributi in blocco utilizzando le code asincrone MySQL. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.3. L&#39;ID della patch è MDVA-31590. Il problema è stato risolto in Adobe Commerce 2.4.2.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0-2.4.1-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli utenti non sono in grado di aggiornare gli attributi in blocco utilizzando MySQL async.

<u>Passaggi da riprodurre</u>:

1. Nella griglia del prodotto nel backend, esegui un’azione di massa per aggiornare i valori degli attributi per alcuni prodotti.
   * Controlla i prodotti e seleziona **Aggiorna attributi** dal menu a discesa Azioni.
1. Imposta i valori per gli attributi richiesti, assegna i prodotti ai siti web e salva.
1. Una volta ricaricata la pagina, verrà visualizzato un messaggio simile al seguente:
   *Task &quot;Update attributes for N selected products&quot; (Aggiorna attributi per N prodotti selezionati): 1 elemento/i pianificato/i per un aggiornamento.*
1. Attendi alcuni secondi e ricarica la pagina backend.

<u>Risultati previsti</u>:

1. Nella pagina viene visualizzato un messaggio di aggiornamento corretto, ad esempio: *1 elemento/i aggiornato/i.*
1. Vengono aggiornati i valori degli attributi dei prodotti correlati.
1. In DB, i nuovi record vengono creati in entrambi `magento_bulk` tabella e `magento_operation` tabella (operazioni relative al gruppo).
1. I nuovi record vengono creati nel `queue_message` tabella (relativa alle code) `product_action_attribute.update` e/o `product_action_attribute.website.update`).
1. `queue_message_status` tabella con record con stato &quot;4&quot;.
1. NON ci sono errori in `system.log`.

<u>Risultati effettivi</u>:

1. Nella pagina viene comunque visualizzato un messaggio simile al seguente:
   *Task &quot;Update attributes for N selected products&quot; (Aggiorna attributi per N prodotti selezionati): 1 elemento/i pianificato/i per un aggiornamento.*
1. I valori degli attributi per i prodotti vengono aggiornati.
1. Viene creato un nuovo record in `message_bulk` tabella, ma non sono presenti record correlati `magento_operation` tabella.
1. I nuovi record vengono creati in `queue_message` e `queue_message_status` tabelle.
1. `queue_message_status` la tabella ha un record con stato di errore (valore di stato &quot;6&quot;).
1. `system.log` contiene un errore simile al seguente:
   *main.CRITICAL: Messaggio rifiutato: SQLSTATE[23000]: violazione del vincolo di integrità: la colonna &quot;operation_key&quot; 1048 non può essere null; query: INSERT INTO {{magento_operation}} ({{id}}, {{bulk_uuid}}, {{topic_name}}, {{serialized_data}}, {{result_serialized_data}}, {{status}}, {{error_code}}, {{result_message}}, {{operation_key}}) VALORI (?, ?, ?, ?, ?, ?, ?, ?, ?) [][]*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento al [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sezione.
