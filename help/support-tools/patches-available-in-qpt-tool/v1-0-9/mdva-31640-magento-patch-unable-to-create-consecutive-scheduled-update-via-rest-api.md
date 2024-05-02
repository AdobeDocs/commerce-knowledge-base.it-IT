---
title: "Patch MDVA-31640: impossibile creare un aggiornamento pianificato consecutivo tramite API REST"
description: La patch MDVA-31640 risolve il problema che impedisce la creazione di un nuovo aggiornamento pianificato per il prezzo speciale per più store utilizzando l'API REST, se la data di inizio dell'aggiornamento coincide con la data di fine dell'aggiornamento esistente. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9. Il problema è stato risolto in Adobe Commerce 2.4.2.
exl-id: 8d91db3d-7c94-4757-8087-4cf53cad81e7
feature: REST
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# Patch MDVA-31640: impossibile creare un aggiornamento pianificato consecutivo tramite API REST

La patch MDVA-31640 risolve il problema che impedisce la creazione di un nuovo aggiornamento pianificato per il prezzo speciale per più store utilizzando l&#39;API REST, se la data di inizio dell&#39;aggiornamento coincide con la data di fine dell&#39;aggiornamento esistente. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9. Il problema è stato risolto in Adobe Commerce 2.4.2.

## Prodotti e versioni interessati

**La patch è stata creata per la versione Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.3.5-p1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce su infrastruttura cloud e Adobe Commerce on-premise 2.3.1 - 2.3.5-p2, 2.4.0, 2.4.0-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

È stato risolto il problema che impediva la creazione di un nuovo aggiornamento pianificato per il prezzo speciale per più store utilizzando l’API REST, se la data di inizio dell’aggiornamento coincide con la data di fine dell’aggiornamento esistente in precedenza.

<u>Passaggi da riprodurre</u>:

1. Imposta una visualizzazione aggiuntiva per sito Web, store e store.
1. Crea due prodotti semplici: &quot;product1&quot; e &quot;product2&quot;.
1. Assegnare product1 a un sito Web e product2 a entrambi i siti Web.
1. Crea un aggiornamento pianificato per il prezzo speciale per il prodotto1 nella visualizzazione punto vendita per il negozio con ID 1. Usa API REST `POST` richiesta a `rest/V1/products/special-price` con il seguente payload:
   `{        "prices": [            {                "price": 15,                "store_id": 1,                "sku": "product1",                "price_from": "2021-11-15 04:00:00",                "price_to": "2021-11-15 04:10:00"            }        ]    }`
1. Crea un aggiornamento pianificato per il prezzo speciale del prodotto2 in entrambe le visualizzazioni dello store per i negozi con ID 1 e 2 utilizzando l’API REST `POST` richiesta a `rest/V1/products/special-price` con il seguente payload (il `price_from` la data è uguale a `price_to` data della richiesta precedente):
   `{        "prices": [            {                "price": 14,                "store_id": 1,                "sku": "product2",                "price_from": "2021-11-15 04:10:00",                "price_to": "2021-11-15 04:15:00"            },            {                "price": 13,                "store_id": 2,                "sku": "product2",                "price_from": "2021-11-15 04:10:00",                "price_to": "2021-11-15 04:15:00"            }        ]    }`

<u>Risultati previsti</u>:

L’aggiornamento pianificato con la modifica del prezzo speciale viene creato in entrambe le visualizzazioni del punto vendita.

<u>Risultati effettivi</u>:

Adobe Commerce genera un errore. Aggiornamento pianificato non creato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento al [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
