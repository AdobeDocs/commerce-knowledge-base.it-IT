---
title: "MDVA-35356: restituzione credito archivio errata dopo l'annullamento dell'ordine parzialmente fatturato"
description: La patch di MDVA-35356 risolve il problema con una restituzione errata del credito all'archivio dopo l'annullamento dell'ordine parzialmente fatturato. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19. L'ID della patch è MDVA-35356. Il problema è stato risolto nella versione 2.4.3 di Adobe Commerce.
exl-id: af37f318-0818-4393-b768-939f08b73847
feature: Invoices, Orders, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---

# MDVA-35356: restituzione credito archivio errata dopo l&#39;annullamento di un ordine parzialmente fatturato

La patch di MDVA-35356 risolve il problema con una restituzione errata del credito all&#39;archivio dopo l&#39;annullamento dell&#39;ordine parzialmente fatturato. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19. L&#39;ID della patch è MDVA-35356. Il problema è stato risolto nella versione 2.4.3 di Adobe Commerce.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.4.1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.3.0-2.4.2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Passaggi da riprodurre</u>:

1. Crea tre prodotti semplici.
1. Crea un nuovo utente e assegna il credito del negozio (Esempio: credito del negozio = *$10,* prezzi del prodotto semplici = *$100*, *$200* e *$300*).
1. Accedi con l’utente sopra indicato e aggiungi i tre prodotti al carrello.
1. Controlla i tre prodotti nel carrello e utilizza il credito del negozio per una parte dell&#39;ordine (ad esempio: pagato con **assegno/vaglia postale**).
1. Eseguire due fatture sull&#39;ordine tramite l&#39;API, una per il prodotto 1 e una per il prodotto 2:

   ```php
   //endpoint POST {\{baseUrl}}/V1/order/:orderId/invoice    //1st API call:    {    "capture": true,    "items": [    {    "order_item_id": 1,    "qty": 1    }    ],    "notify": true,    "appendComment": false    }    //2nd API call:    {    "capture": true,    "items": [    {    "order_item_id": 2,    "qty": 1    }    ],    "notify": true,    "appendComment": false    }
   ```

1. Si noti che il credito del negozio viene applicato completamente alla prima fattura.
1. &#x200B;Si noti che il saldo del credito dell&#39;archivio = *0*.
1. Annullare l&#39;ordine e verificare che due articoli siano fatturati e che il terzo articolo sia annullato.
1. Osservare il saldo del credito del negozio.

<u>Risultati previsti</u>:

Il saldo del credito del negozio è ancora 0 perché il credito del negozio di 10 $ è stato fatturato.

<u>Risultati effettivi</u>:

Viene restituito l&#39;intero credito del negozio: il saldo è di $10.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
