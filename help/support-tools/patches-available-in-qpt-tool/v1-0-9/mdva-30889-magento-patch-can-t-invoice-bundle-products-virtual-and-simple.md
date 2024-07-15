---
title: "MDVA-30889: impossibile fatturare prodotti bundle virtuali e semplici"
description: La patch MDVA-30889 risolve il problema relativo alla presenza di un errore dopo la fatturazione di un prodotto bundle con opzioni sia virtuali che semplici. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9. Il problema è stato risolto in Adobe Commerce 2.4.2.
exl-id: 7e6555c5-9088-4c85-920d-20c841ad6675
feature: Invoices, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# MDVA-30889: impossibile fatturare prodotti bundle virtuali e semplici

La patch MDVA-30889 risolve il problema relativo alla presenza di un errore dopo la fatturazione di un prodotto bundle con opzioni sia virtuali che semplici. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9. Il problema è stato risolto in Adobe Commerce 2.4.2.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.4.1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Prerequisiti</u>:

Installa Adobe Commerce con [Inventory management](https://devdocs.magento.com/guides/v2.4/inventory/).

<u>Passaggi da riprodurre</u>:

1. Vai a **Amministratore**.
1. Crea un prodotto semplice.
1. Creare un prodotto virtuale.
1. Crea un prodotto bundle (crea due opzioni a discesa per i prodotti secondari e assegna prodotti virtuali e semplici). Imposta **Prezzo dinamico** = *No*.
1. Vai alla vetrina.
1. Vai alla pagina del prodotto.
1. Aggiungi il prodotto al carrello.
1. Procedi al pagamento e ordina il prodotto.
1. Vai a **Amministratore > Ordini**.
1. Aprire l&#39;ordine creato e fatturarlo.

<u>Risultati previsti</u>:

Viene creata la fattura di un prodotto bundle (che contiene prodotti semplici e virtuali).

<u>Risultati effettivi</u>:

La fattura non viene creata e viene visualizzato un messaggio di errore simile al seguente:

```php
TypeError: Return value of Magento\InventorySourceSelection\Model\Request\InventoryRequest::getItems() must be of the type array, null returned in vendor/magento/module-inventory-source-selection/Model/Request/InventoryRequest.php:102
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
