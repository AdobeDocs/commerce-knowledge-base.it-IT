---
title: "MDVA-30565: problema di archiviazione locale e checkout della cache di sessione"
description: La patch MDVA-30565 risolve il problema relativo all'archiviazione e al check-out locali della cache di sessione. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6.
exl-id: f0693f0c-fc6b-44af-a6a0-ebfa973bca65
feature: Cache, Checkout, Orders, Storage
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# MDVA-30565: problema di archiviazione locale e checkout della cache di sessione

La patch MDVA-30565 risolve il problema relativo all&#39;archiviazione e al check-out locali della cache di sessione. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce sull’infrastruttura cloud 2.3.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.2 - 2.3.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli elementi del carrello possono ancora essere visualizzati nella pagina del carrello quando una sessione del cliente scade. Questo causa un errore nel metodo di spedizione della stima se non sono disponibili metodi di spedizione per il pagamento guest.

<u>Passaggi da riprodurre</u>:

1. Abilita il carrello acquisti permanente nell’amministratore di Commerce. (**Abilita persistenza** = &quot;*Sì*&quot;)
1. Accedi come cliente nel front-end. In questo modo viene creato `persistent_shopping_cart` e avvia una sessione persistente.
1. Aggiungi un prodotto al carrello.
1. Attendi il timeout della sessione front-end o elimina `PHPSESSID` cookie.
1. Ora sei un utente ospite, ma se vai al carrello, puoi ancora vedere il prodotto aggiunto come cliente connesso.
1. Rimuovi il prodotto dal carrello, che ora è vuoto. Puoi vedere Adobe Commerce eliminare `persistent_shopping_cart` cookie in questo evento.
1. Aggiungi un nuovo prodotto al carrello e passa alla pagina del carrello.
1. Ora viene visualizzato nella console del browser `V1/guest-carts/4/estimate-shipping-methods` request now restituisce una risposta 404 con un messaggio `{"message":"No such entity        with %fieldName = %fieldValue","parameters":{"fieldName":"cartId","fieldValue":0}}`

<u>Risultati previsti</u>:

La richiesta del metodo di spedizione della stima restituisce risultati corretti.

<u>Risultati effettivi</u>:

La richiesta del metodo di spedizione della stima non riesce e viene visualizzato un errore simile a &quot;*Non sono disponibili preventivi per questo ordine in questo momento.*&quot;

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
