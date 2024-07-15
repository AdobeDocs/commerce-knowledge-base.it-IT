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

La patch MDVA-31590 risolve il problema che impediva agli utenti di aggiornare gli attributi in blocco utilizzando le code asincrone MySQL. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.3. L&#39;ID della patch è MDVA-31590. Il problema è stato risolto in Adobe Commerce 2.4.2.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0-2.4.1-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli utenti non sono in grado di aggiornare gli attributi in blocco utilizzando MySQL async.

<u>Passaggi da riprodurre</u>:

1. Nella griglia del prodotto nel backend, esegui un’azione di massa per aggiornare i valori degli attributi per alcuni prodotti.
   * Controlla i prodotti e seleziona **Aggiorna attributi** dal menu a discesa Azioni.
1. Imposta i valori per gli attributi richiesti, assegna i prodotti ai siti web e salva.
1. Una volta ricaricata la pagina, verrà visualizzato un messaggio simile al seguente:
   *Attività &quot;Aggiorna attributi per N prodotti selezionati&quot;: 1 elemento/i pianificato/i per un aggiornamento.*
1. Attendi alcuni secondi e ricarica la pagina backend.

<u>Risultati previsti</u>:

1. Nella pagina viene visualizzato un messaggio di aggiornamento come: *1 elemento/i aggiornato/i correttamente.*
1. Vengono aggiornati i valori degli attributi dei prodotti correlati.
1. Nel database vengono creati nuovi record sia nella tabella `magento_bulk` che nella tabella `magento_operation` (operazioni relative al bulk).
1. Nuovi record creati nella tabella `queue_message` (relativi alle code `product_action_attribute.update` e/o `product_action_attribute.website.update`).
1. La tabella `queue_message_status` contiene record con stato &quot;4&quot;.
1. NESSUN errore in `system.log`.

<u>Risultati effettivi</u>:

1. Nella pagina viene comunque visualizzato un messaggio simile al seguente:
   *Attività &quot;Aggiorna attributi per N prodotti selezionati&quot;: 1 elemento/i pianificato/i per un aggiornamento.*
1. I valori degli attributi per i prodotti vengono aggiornati.
1. Un nuovo record viene creato nella tabella `message_bulk`, ma non sono presenti record correlati nella tabella `magento_operation`.
1. Nuovi record creati nelle tabelle `queue_message` e `queue_message_status`.
1. La tabella `queue_message_status` ha un record con stato di errore (valore di stato &quot;6&quot;).
1. `system.log` contiene un errore simile al seguente:
   *main.CRITICAL: messaggio rifiutato: SQLSTATE[23000]: violazione del vincolo di integrità: la colonna &#39;operation_key&#39; 1048 non può essere Null, la query era: INSERT INTO {{magento_operation}} ({{id}}, {{bulk_uuid}}, {{topic_name}}, {{serialized_data}}, {{result_serialized_data}}, {{status}}, {{error_code}}, {{result_message}}, {{operation_key}}) VALORI (?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?) [][]*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
