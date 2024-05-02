---
title: '''MDVA-43414: errore irreversibile PHP durante l''esecuzione di "inventory.Reservation.updateSalabilityStatus"'''
description: La patch MDVA-43414 risolve l’errore irreversibile PHP che si verifica durante l’esecuzione del consumer di coda "inventory.Reservation.updateSalabilityStatus" sugli SKU numerici. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12. L'ID della patch è MDVA-43414. Il problema è stato risolto in Adobe Commerce 2.4.2.
exl-id: 197c5db1-36bc-41a7-a5ca-f026600da786
feature: Inventory, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# MDVA-43414: errore irreversibile PHP durante l&#39;esecuzione di &quot;inventory.Reservation.updateSalabilityStatus&quot;

La patch MDVA-43414 risolve l&#39;errore irreversibile PHP che si verifica durante l&#39;esecuzione di `inventory.reservations.updateSalabilityStatus` mette in coda il consumatore negli SKU numerici. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12. L&#39;ID della patch è MDVA-43414. Il problema è stato risolto in Adobe Commerce 2.4.2.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.6-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.6 - 2.3.7-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Si verifica un errore irreversibile PHP durante l’esecuzione del consumer di code &quot;inventory.Reservations.updateSalabilityStatus&quot; su SKU numeriche.

<u>Prerequisiti</u>:

Moduli inventario installati.

<u>Passaggi da riprodurre</u>:

1. Creare un&#39;origine di magazzino personalizzata e assegnarla a una nuova scorta di magazzino.
1. Crea un prodotto con origine inventario personalizzata.
1. Assicurati che lo SKU del prodotto sia un valore intero.
1. Effettua un ordine.
1. Esegui il `bin/magento queue:consumer:start inventory.reservations.updateSalabilityStatus` comando.

<u>Risultati previsti</u>:

La coda viene avviata senza errori.

<u>Risultati effettivi</u>:

Si verifica un errore irreversibile PHP:

```PHP
PHP Fatal error:  Uncaught TypeError: Argument 1 passed to Magento\InventoryIndexer\Model\Queue\UpdateIndexSalabilityStatus\IndexProcessor::getIndexSalabilityStatus() must be of the type string, int given, called in /vendor/magento/module-inventory-indexer/Model/Queue/UpdateIndexSalabilityStatus/IndexProcessor.php on line 119 and defined in /vendor/magento/module-inventory-indexer/Model/Queue/UpdateIndexSalabilityStatus/IndexProcessor.php:136
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
