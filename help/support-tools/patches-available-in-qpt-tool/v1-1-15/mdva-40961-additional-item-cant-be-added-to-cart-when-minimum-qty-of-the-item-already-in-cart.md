---
title: "MDVA-40961: impossibile aggiungere al carrello un elemento aggiuntivo quando la quantità minima di elemento è già nel carrello"
description: La patch MDVA-40961 risolve il problema che impedisce l'aggiunta di un articolo al carrello quando la quantità minima dell'articolo è già nel carrello. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15. L'ID della patch è MDVA-40961. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
exl-id: fc90c2b6-f631-49ff-81b0-e41918dd79a7
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-40961: impossibile aggiungere al carrello un elemento aggiuntivo quando la quantità minima di elemento è già nel carrello

La patch MDVA-40961 risolve il problema che impedisce l&#39;aggiunta di un articolo al carrello quando la quantità minima dell&#39;articolo è già nel carrello. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15. L&#39;ID della patch è MDVA-40961. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.3-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Impossibile aggiungere un articolo aggiuntivo al carrello se la quantità minima dell&#39;articolo è già nel carrello.

<u>Passaggi da riprodurre</u>:

1. Impostare un prodotto semplice in modo che ne abbia più di uno **Quantità minima consentita nel carrello** (ad esempio, due).
1. Apri il prodotto sullo Storefront e aggiungine due al carrello.
1. Rimani nella pagina del prodotto e aggiungi un altro prodotto al carrello.

<u>Risultati previsti</u>:

Il terzo prodotto può essere aggiunto al carrello in quanto contiene già la quantità minima.

<u>Risultati effettivi</u>:

Viene visualizzato il seguente messaggio di errore: *Il minor numero possibile di acquisti è 2*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
