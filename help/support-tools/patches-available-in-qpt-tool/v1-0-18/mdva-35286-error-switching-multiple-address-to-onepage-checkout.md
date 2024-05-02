---
title: "MDVA-35286: errore durante il passaggio da Multiple Address a Onepage checkout"
description: La patch MDVA-35286 risolve il problema relativo alla presenza di un errore se un cliente dispone di prodotti bundle nel carrello e passa dal pagamento tramite più indirizzi al pagamento tramite Onepage. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18. L'ID della patch è MDVA-35286. Il problema è stato risolto in Adobe Commerce 2.4.2.
exl-id: 40c98735-6054-4b25-9882-e274424b203f
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# MDVA-35286: errore durante il passaggio da Multiple Address a Onepage checkout

La patch MDVA-35286 risolve il problema relativo alla presenza di un errore se un cliente dispone di prodotti bundle nel carrello e passa dal pagamento tramite più indirizzi al pagamento tramite Onepage. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18. L&#39;ID della patch è MDVA-35286. Il problema è stato risolto in Adobe Commerce 2.4.2.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.4.1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.0-2.4.1-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Se nel carrello è presente un prodotto bundle e l’utente tenta di utilizzare il Checkout di una pagina dopo aver abbandonato il Checkout di più spedizioni, viene visualizzato un errore.

<u>Passaggi da riprodurre</u>:

1. Accedi all’account del cliente e aggiungi più di un prodotto bundle al carrello.
1. Fai clic sul collegamento per visualizzare e modificare il carrello.
1. Fai clic su **Check-Out con più indirizzi** collegamento.
1. Seleziona indirizzi diversi per i prodotti aggiunti al carrello.
1. Clic **Torna al carrello**.
1. Nel carrello, fai clic su **Procedi all&#39;estrazione**.

<u>Risultati previsti</u>:

Viene reindirizzato alla pagina Pagamento.

<u>Risultati effettivi</u>:

Viene visualizzato il messaggio di errore: *Si è verificato un errore durante l&#39;elaborazione della richiesta*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
