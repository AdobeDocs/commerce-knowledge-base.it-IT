---
title: "ACSD-45424: Compensazione prenotazione errata creata dopo rimborso parziale"
description: La patch ACSD-45424 risolve il problema che comporta la creazione di una compensazione della prenotazione non corretta dopo un rimborso parziale. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17. L’ID della patch è ACSD-45424. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.
exl-id: 0676cfda-a28e-4a66-a75b-8a3fc5e22566
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---

# ACSD-45424: Compensazione prenotazione errata creata dopo rimborso parziale

La patch ACSD-45424 risolve il problema che comporta la creazione di una compensazione della prenotazione non corretta dopo un rimborso parziale. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17. L’ID della patch è ACSD-45424. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.4 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La compensazione della prenotazione non corretta viene creata dopo un rimborso parziale.

<u>Passaggi da riprodurre</u>:

1. Abilita il metodo di spedizione della consegna in-store.
1. Creare tre origini magazzino e assicurarsi che l&#39;ubicazione di prelievo sia attiva in ciascuna (origine1, origine2, origine3).
1. Create un nuovo materiale e assegnate le tre origini al nuovo materiale.
   * Questo stock deve essere assegnato al sito web principale.
1. Create un prodotto semplice, P3, e assegnate ad esso tutte le sorgenti.
1. Aggiungi le seguenti quantità per le origini del prodotto semplice e abilita ordini inevasi:
   * Origine predefinita - 100
   * source1 - 0
   * source2 - 10
   * source3 - 0
1. Aggiungi il prodotto semplice al carrello dal front-end e procedi al modulo di spedizione.
1. Selezionare &quot;source1&quot; come ubicazione di spedizione.
1. Completa l’ordine ed esegui la seguente query nel database:

   ```sql
   SELECT * FROM inventory_reservation WHERE sku = 'P3';
   ```

   Riceverai il record dell’ordine effettuato nella `inventory_reservation` tabella. La quantità è 10, che è corretta.
1. Fattura questo ordine dal backend.
1. Ora crea una nota di credito per un solo prodotto. NON selezionare *Torna all&#39;archivio* casella di controllo.
1. Esegui la stessa query dal passaggio 8.

<u>Risultati previsti</u>:

Se non hai selezionato *Torna all&#39;archivio* durante la creazione della nota di credito, il `inventory_reservation` la tabella non avrà un record corrispondente alla nota di credito.

<u>Risultati effettivi</u>:

Anche se non hai selezionato il *Torna all&#39;archivio* durante la creazione della nota di credito, aggiunge un record a `inventory_reservation` tabella con `creditmemo_created` tipo di evento. Inoltre, il record della nota di accredito aggiunto nel `inventory_reservation` la tabella ha una quantità pari a 10 anche se è stata creata la nota di accredito per una sola quantità.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
