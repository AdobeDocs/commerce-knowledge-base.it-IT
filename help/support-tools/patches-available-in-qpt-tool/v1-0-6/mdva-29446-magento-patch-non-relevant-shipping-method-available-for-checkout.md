---
title: "MDVA-29446: metodo di spedizione non pertinente disponibile per il pagamento"
description: La patch MDVA-29446 risolve il problema relativo alla visualizzazione di un metodo di spedizione non applicabile nelle opzioni del metodo di spedizione di pagamento e, se selezionata, un messaggio di errore "*Gestore con tale metodo non trovato nullo, tariffa fissa*". visualizzazioni. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6. Il problema è pianificato per essere risolto nelle versioni successive di Adobe Commerce.
exl-id: 74de5ec4-1f57-4d63-8fbc-614b23783ee3
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# MDVA-29446: metodo di spedizione non pertinente disponibile per il pagamento

La patch MDVA-29446 risolve il problema relativo alla visualizzazione di un metodo di spedizione non applicabile nelle opzioni del metodo di spedizione e, se selezionato, di un messaggio di errore &quot;*Il gestore con tale metodo non è stato trovato nullo, con tariffa fissa*.&quot; visualizzazioni. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6. Il problema è pianificato per essere risolto nelle versioni successive di Adobe Commerce.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce sull’infrastruttura cloud 2.3.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.3-2.4.0.

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problemi

Hai un metodo di spedizione che non è applicabile, ma viene comunque visualizzato nelle opzioni del metodo di spedizione di pagamento, e puoi selezionare questo metodo di spedizione non rilevante.

<u>Passaggi da riprodurre</u>:

1. Installare clean 2.3-development.
1. Attiva tariffa fissa e imposta:

   * Spedisci a paesi applicabili = *Paesi specifici*
   * Spedisci a paesi specifici = *Antartide*
   * Mostra metodo se non applicabile = *Sì*

1. Disattiva tutti gli altri metodi di spedizione.
1. Vai al front-end e crea un cliente con un indirizzo negli Stati Uniti.
1. Seleziona un elemento e fai clic su **Aggiungi al carrello**.
1. Fai clic sul carrello e fai clic su **Procedi all&#39;estrazione**.

<u>Risultati effettivi</u>:

1. Il giorno **Spedizione** pagina, vengono visualizzati i seguenti elementi:

   * Tariffa fissa visibile
   * Tariffa fissa: $0
1. Dopo che l’utente fa clic su **Successivo**, l’utente riceve il seguente errore:

*&quot;Impossibile trovare il gestore con questo metodo: null, flatrate&quot;*

<u>Risultati previsti</u>:

* Il prezzo del metodo di spedizione non è visibile se il metodo di spedizione non è applicabile.
* Il **Successivo** non deve essere attivo.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
