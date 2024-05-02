---
title: "MDVA-40609: dati dei prodotti disabilitati assenti nella tabella cataloginventory_stock_status"
description: La patch MDVA-40609 risolve il problema per cui i dati dei prodotti disabilitati non vengono visualizzati nella tabella di indice "cataloginventory_stock_status", causando la visualizzazione di quantità di prodotti errate. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6. L'ID della patch è MDVA-40609. Il problema è stato risolto in Adobe Commerce 2.4.3.
exl-id: 2424c3b3-8bc9-4dd4-908c-9d653f09a57a
feature: Catalog Management, Inventory, Orders, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-40609: dati dei prodotti disabilitati assenti nella tabella cataloginventory_stock_status

La patch MDVA-40609 risolve il problema se i dati dei prodotti disabilitati non vengono visualizzati nella `cataloginventory_stock_status` tabella indice che porta alla visualizzazione di quantità di prodotto errate. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6. L&#39;ID della patch è MDVA-40609. Il problema è stato risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I dati dei prodotti disattivati non vengono visualizzati nella `cataloginventory_stock_status` tabella indice che porta alla visualizzazione di quantità di prodotto errate.

<u>Prerequisiti</u>:

Il modulo Inventario è installato.

<u>Passaggi da riprodurre</u>:

1. Configura due siti Web con store e visualizzazioni dello store.
1. Create un&#39;origine e un magazzino aggiuntivi.
1. Aggiungi un prodotto semplice:
   * Imposta Abilita prodotto su *No*.
   * Assegna due origini con Stato articolo origine = Instock e Qtà maggiori di zero.
1. Salva il prodotto.
1. Controlla la **Quantità vendibile prodotto** scheda.

<u>Risultati previsti</u>:

Entrambi gli stock hanno un valore superiore a zero.

<u>Risultati effettivi</u>:

Un titolo ha valore zero.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento al [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sezione.
