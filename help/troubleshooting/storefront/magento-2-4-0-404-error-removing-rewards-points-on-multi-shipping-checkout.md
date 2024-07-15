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

Questo articolo fornisce una soluzione alternativa per un problema noto in Adobe Commerce 2.4.0 relativo a un errore di pagina Web &quot;*404 Non trovato*&quot; durante la rimozione dei punti premio in una pagina di pagamento con spedizione multipla. Attualmente, nella pagina di pagamento per più spedizioni, quando si tenta di rimuovere i punti premio utilizzati per pagare un ordine, viene visualizzata una pagina &quot;*404 Non trovato*&quot; invece dell&#39;annullamento dei punti premio. Questo problema verrà risolto in con una versione patch di Adobe Commerce 2.4.1.

## Prodotti e versioni interessati

* Adobe Commerce 2.4.0 (tutti i metodi di distribuzione)

## Problema

<u>Passaggi da riprodurre</u>

1. Passa alla vetrina e accedi come cliente.
1. Aggiungi almeno due prodotti al **carrello**.
1. Apri il **Mini-carrello**.
1. Fare clic sul collegamento **Visualizza e modifica carrello**.
1. Fare clic sul collegamento **Estrai con più indirizzi**.
1. Selezionare gli indirizzi di spedizione nella pagina **Spedisci a più indirizzi**.
1. Fare clic sul pulsante **Vai alle informazioni sulla spedizione**.
1. Selezionare **Tariffa fissa - Metodo di spedizione fisso** per ogni indirizzo.
1. Fai clic sul pulsante **Continua con informazioni fatturazione**.
1. Seleziona la casella di controllo **Utilizza i tuoi punti premio** nella pagina **Informazioni di fatturazione**.
1. Fai clic sul pulsante **Vai a controllare l&#39;ordine**.
1. Fare clic sul collegamento **Rimuovi** per qualsiasi indirizzo per rimuovere i punti premio.

<u>Risultati previsti</u>

* Viene visualizzata la pagina **Carrello acquisti**.
* &quot;*Hai rimosso i punti premio da questo ordine.Il messaggio*&quot; dovrebbe essere visualizzato.

<u>Risultato effettivo</u>

Viene visualizzata una pagina di errore &quot;*404 Non trovato*&quot;.

## Soluzione alternativa

La soluzione consiste nel far tornare l&#39;acquirente al **carrello** e rimuovere i punti premio dalla pagina Web **carrello**. Il problema dovrebbe essere risolto con la patch di Adobe Commerce versione 2.4.1, il cui rilascio è pianificato per il quarto trimestre del 2020.

## Lettura correlata

* [Problema noto di Adobe Commerce 2.4.0: l’aggiornamento delle attività del cliente non funziona](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0 Problema noto: visualizzazione dei dati dei messaggi non elaborati in Storefront](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Problema noto di Adobe Commerce 2.4.0: l’esportazione delle aliquote fiscali non funziona](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [L’amministratore B2B di Adobe Commerce 2.4.0 non può aggiungere un prodotto configurabile all’offerta](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Adobe Commerce 2.4.0 problema noto: errore di visualizzazione degli ordini](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
