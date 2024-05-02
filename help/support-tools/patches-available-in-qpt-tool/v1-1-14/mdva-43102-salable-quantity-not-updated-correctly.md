---
title: "MDVA-43102: quantità vendibile non aggiornata correttamente"
description: La patch MDVA-43102 risolve il problema che causa l'aggiornamento non corretto della quantità vendibile quando viene effettuato un rimborso tramite API REST. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14. L'ID della patch è MDVA-43102. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
exl-id: c51bc45b-a7e0-4581-a318-9c4736e6661c
feature: Variables
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# MDVA-43102: quantità di vendita non aggiornata correttamente

La patch MDVA-43102 risolve il problema che causa l&#39;aggiornamento non corretto della quantità vendibile quando viene effettuato un rimborso tramite API REST. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14. L&#39;ID della patch è MDVA-43102. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.1 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La quantità vendibile non viene aggiornata correttamente quando viene effettuato un rimborso utilizzando l’API REST.

<u>Passaggi da riprodurre</u>:

1. Aggiungi un articolo al carrello.
1. Controllare la Qtà magazzino e la Qtà vendibile.
1. Crea un ordine.
1. Creare una fattura, se necessario.
1. Sottomettere una richiesta REST per rimborsare la fattura utilizzando il seguente payload:

   * metodo/ordine offline/`<order_id>`/rimborso
   * metodo online/fattura/`<invoice_id>`/rimborso

   ```rest
   {
     "items": [
     {
       "order_item_id": <order_item_id>,
       "qty": 1
     }
     ],
     "notify": true,
     "arguments": {
       "shipping_amount": 5,
       "extension_attributes": {
         "return_to_stock_items": [
         <order_item_id>
         ]
       }
     }
   }
   ```

1. Non spedire gli articoli.
1. Confrontare la Qtà magazzino e la Qtà vendibile da prima. Entrambi devono essere aggiornati dello stesso importo.

<u>Risultati previsti</u>:

La quantità vendibile viene aggiornata correttamente quando viene emesso un rimborso prima della spedizione dell&#39;ordine e il prodotto viene restituito alle scorte.

<u>Risultati effettivi</u>:

La quantità vendibile non viene aggiornata quando viene emesso un rimborso prima della spedizione dell&#39;ordine e il prodotto viene restituito alle scorte.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
