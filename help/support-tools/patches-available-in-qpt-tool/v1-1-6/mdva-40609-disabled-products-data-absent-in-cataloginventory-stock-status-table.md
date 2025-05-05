---
title: 'MDVA-40609: dati dei prodotti disabilitati assenti nella tabella cataloginventory_stock_status'
description: La patch MDVA-40609 risolve il problema per cui i dati dei prodotti disabilitati non vengono visualizzati nella tabella di indice "cataloginventory_stock_status", causando la visualizzazione di quantità di prodotti errate. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6. L'ID della patch è MDVA-40609. Il problema è stato risolto in Adobe Commerce 2.4.3.
exl-id: 2424c3b3-8bc9-4dd4-908c-9d653f09a57a
feature: Catalog Management, Inventory, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-40609: dati dei prodotti disabilitati assenti nella tabella cataloginventory_stock_status

La patch MDVA-40609 risolve il problema che causa la mancata visualizzazione dei dati dei prodotti disabilitati nella tabella dell&#39;indice `cataloginventory_stock_status`, causando la visualizzazione di quantità di prodotti errate. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6. L&#39;ID della patch è MDVA-40609. Il problema è stato risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I dati dei prodotti disattivati non vengono visualizzati nella tabella dell&#39;indice `cataloginventory_stock_status` e le quantità dei prodotti non sono corrette.

<u>Prerequisiti</u>:

Il modulo Inventario è installato.

<u>Passaggi da riprodurre</u>:

1. Configura due siti Web con store e visualizzazioni dello store.
1. Create un&#39;origine e un magazzino aggiuntivi.
1. Aggiungi un prodotto semplice:
   * Impostare Abilita prodotto su *No*.
   * Assegna due origini con Stato articolo Source = Instock e Qtà maggiori di zero.
1. Salva il prodotto.
1. Controlla la scheda **Quantità venduta prodotto**.

<u>Risultati previsti</u>:

Entrambi gli stock hanno un valore superiore a zero.

<u>Risultati effettivi</u>:

Un titolo ha valore zero.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
