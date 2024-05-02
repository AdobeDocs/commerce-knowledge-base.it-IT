---
title: "Adobe Commerce 2.4.0: errore 404 durante la rimozione dei punti premio in caso di pagamento con spedizione multipla"
description: Questo articolo fornisce una soluzione alternativa per un problema noto in Adobe Commerce 2.4.0 relativo a un errore di pagina web "*404 Non trovato*" durante la rimozione di punti premio in una pagina di pagamento con spedizione multipla. Attualmente, nella pagina di pagamento multi-shipping, quando si tenta di rimuovere i punti premio utilizzati per pagare un ordine, viene visualizzata una pagina "*404 Non trovato*" invece dell’annullamento riuscito dei punti premio. Questo problema verrà risolto in con una versione patch di Adobe Commerce 2.4.1.
exl-id: 59de4b3d-af28-4ae8-8f55-4ec958e6ee8b
feature: B2B, Checkout, Orders, Rewards, Shipping/Delivery, Storefront
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: errore 404 durante la rimozione dei punti premio durante il pagamento con più spedizioni

Questo articolo fornisce una soluzione alternativa per un problema noto in Adobe Commerce 2.4.0 per un’&quot;*404 Non trovato*&quot;errore di pagina web durante la rimozione dei punti premio in una pagina di pagamento con più spedizioni. Attualmente, nella pagina di pagamento multi-shipping, quando si tenta di rimuovere i punti premio utilizzati per pagare un ordine, viene visualizzato un messaggio di tipo &quot;*404 Non trovato* Viene visualizzata la pagina &quot; invece dell’annullamento dei punti premio. Questo problema verrà risolto in con una versione patch di Adobe Commerce 2.4.1.

## Prodotti e versioni interessati

* Adobe Commerce 2.4.0 (tutti i metodi di distribuzione)

## Problema

<u>Passaggi da riprodurre</u>

1. Passa alla vetrina e accedi come cliente.
1. Aggiungi almeno due prodotti al **Carrello**.
1. Apri **Mini-carrello**.
1. Fai clic su **Visualizza e modifica carrello** collegamento.
1. Fai clic su **Check-Out con più indirizzi** collegamento.
1. Seleziona gli indirizzi di spedizione nella **Spedisci a più indirizzi** pagina.
1. Fai clic su **Vai a Informazioni spedizione** pulsante.
1. Seleziona la **Tariffa fissa - Metodo di spedizione fisso** per ogni indirizzo.
1. Fai clic su **Continua con le informazioni di fatturazione** pulsante.
1. Controlla la **Utilizzare i punti premio** casella di controllo sulla **Informazioni fatturazione** pagina.
1. Fai clic su **Vai a rivedere l&#39;ordine** pulsante.
1. Fai clic su **Rimuovi** collegamento per qualsiasi indirizzo per rimuovere i punti premio.

<u>Risultati previsti</u>

* Il **Carrello** dovrebbe essere visualizzata.
* La &quot;*Hai rimosso i punti premio da questo ordine.* Dovrebbe apparire il messaggio &quot;.

<u>Risultato effettivo</u>

A &quot;*404 Non trovato* Viene visualizzata la pagina di errore &quot;.

## Soluzione alternativa

La soluzione consiste nel far sì che l&#39;acquirente torni al **Carrello** e rimuovere i punti premio dal **Carrello** pagina web. Il problema dovrebbe essere risolto con la patch di Adobe Commerce versione 2.4.1, il cui rilascio è pianificato per il quarto trimestre del 2020.

## Lettura correlata

* [Problema noto di Adobe Commerce 2.4.0: l’aggiornamento delle attività del cliente non funziona](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0 Problema noto: visualizzazione dei dati dei messaggi non elaborati in Storefront](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Problema noto di Adobe Commerce 2.4.0: l’esportazione delle aliquote fiscali non funziona](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [L’amministratore B2B di Adobe Commerce 2.4.0 non può aggiungere un prodotto configurabile all’offerta](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Adobe Commerce 2.4.0 problema noto: errore di visualizzazione degli ordini](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
