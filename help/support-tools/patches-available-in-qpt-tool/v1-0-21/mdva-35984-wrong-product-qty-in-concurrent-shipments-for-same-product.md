---
title: "MDVA-35984: quantità di prodotto errata nelle spedizioni simultanee per lo stesso prodotto"
description: La patch MDVA-35984 risolve il problema quando si creano più spedizioni simultanee per lo stesso prodotto, dando una quantità di prodotto (Qtà) errata. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21. L'ID della patch è MDVA-35984. Il problema è stato risolto in Adobe Commerce 2.4.3.
exl-id: b15e25e1-c451-4350-950d-ae4893835e54
feature: Orders, Products, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# MDVA-35984: quantità di prodotto errata nelle spedizioni simultanee per lo stesso prodotto

La patch MDVA-35984 risolve il problema quando si creano più spedizioni simultanee per lo stesso prodotto, dando una quantità di prodotto (Qtà) errata. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21. L&#39;ID della patch è MDVA-35984. Il problema è stato risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.0-2.4.2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto semplice con **Qtà** = *100*.
1. Crea due ordini con questo prodotto.
1. Effettuare chiamate API simultanee per creare spedizioni per entrambi gli ordini, come nell’esempio seguente:

   ```php
   POST <host>/rest/<store_code>/V1/order/3/ship    ```    where **order id** = *3* , with a payload like:    ```php    {        "items": [            {                "order_item_id": <order_item_id>,                "qty": 1            }        ],        "tracks": [            {                "track_number": "1Y-9876543210",                "title": "United Parcel Service",                "carrier_code": "ups"            }        ]    }
   ```

1. Controllare la quantità di prodotto nella griglia di amministrazione.

<u>Risultati previsti</u>:

Il risultato è il prodotto **Qtà** = *98* dopo entrambe le spedizioni.

<u>Risultati effettivi</u>:

Il risultato è il prodotto **Qtà** = *99* dopo entrambe le spedizioni.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
