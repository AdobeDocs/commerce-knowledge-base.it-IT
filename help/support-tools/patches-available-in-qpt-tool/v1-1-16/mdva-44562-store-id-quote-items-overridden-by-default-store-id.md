---
title: "MDVA-44562: ID archivio per gli elementi dell'offerta sovrascritto dall'ID archivio predefinito"
description: La patch MDVA-44562 risolve il problema per cui l'ID archivio predefinito sostituisce l'ID archivio per gli elementi di preventivo per le richieste GraphQL. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16. L'ID della patch è MDVA-44562. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.
exl-id: 902bfc05-411d-4a6c-a6e8-cd7376629b0c
feature: Quotes
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# MDVA-44562: ID archivio per gli elementi dell&#39;offerta sostituito dall&#39;ID archivio predefinito

La patch MDVA-44562 risolve il problema per cui l&#39;ID archivio predefinito sostituisce l&#39;ID archivio per gli elementi di preventivo per le richieste GraphQL. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16. L&#39;ID della patch è MDVA-44562. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’ID archivio per gli elementi dell’offerta viene sostituito dall’ID archivio predefinito per le richieste GraphQL.

<u>Passaggi da riprodurre</u>:

1. Crea una nuova visualizzazione store.
1. Crea un nuovo prodotto semplice con nomi diversi per ogni visualizzazione store.
1. Crea un nuovo cliente.
1. Ottieni il token di autorizzazione del cliente.

   ```GraphQL
    POST /rest/all/V1/integration/customer/token
    {
      "username": "test@example.com",
      "password": "password"
     }
   ```

1. Crea un nuovo preventivo per il cliente utilizzando il token di autorizzazione.

   ```GraphQL
   POST rest/default/V1/carts/mine
   ```

1. Aggiungi un prodotto al carrello.

   ```GraphQL
   POST /rest/default/V1/carts/mine/items
   {
     "cartItem": {
       "sku": "simple1",
       "qty": 1,
       "quote_id": "1"
     }
   }
   ```

1. Ottieni il contenuto del carrello per la visualizzazione predefinita dello store.

   ```GraphQL
   GET rest/default/V1/carts/mine/
   ```

1. Ottieni il contenuto del carrello per la nuova visualizzazione Store.

   ```GraphQL
   GET rest/<store_view_2>/V1/carts/mine/
   ```

<u>Risultati previsti</u>:

La risposta dalla nuova visualizzazione Store mostra il nome del prodotto dalla nuova visualizzazione Store.

<u>Risultati effettivi</u>:

La risposta dalla nuova vista Store mostra l’impostazione del nome del prodotto nella vista Store predefinita.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella documentazione per gli sviluppatori.
