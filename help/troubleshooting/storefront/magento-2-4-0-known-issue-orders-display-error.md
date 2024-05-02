---
title: "Problema noto di Adobe Commerce 2.4.0: errore di visualizzazione degli ordini"
description: '"Questo articolo fornisce una soluzione alternativa per un problema noto in Adobe Commerce per un errore di visualizzazione degli ordini. Quando i clienti connessi esaminano i propri ordini nel menu **Il mio account** (**Il mio account &gt; I miei ordini**), la griglia degli ordini non è in grado di portare il numero di ordini per pagina a 20 dalla pagina 2 quando sono presenti 11 ordini. Inoltre, se ci sono più ordini di quelli configurati per la visualizzazione per pagina, quando si passa all’ultima pagina con gli ordini, la modifica del numero di ordini mostrati per pagina genera il messaggio di errore: *Non hai effettuato alcun ordine*. Questo problema verrà risolto in Adobe Commerce 2.4.1.'''
exl-id: a6d300e1-1cbc-42b9-997d-d72f8765517b
feature: B2B, Categories, Storefront
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# Problema noto di Adobe Commerce 2.4.0: errore di visualizzazione degli ordini

Questo articolo fornisce una soluzione alternativa per un problema noto in Adobe Commerce per un errore di visualizzazione degli ordini. Quando i clienti hanno effettuato l’accesso, esaminano i loro ordini in **Il mio account** menu (**Account > Ordini personali**), la griglia ordini non è in grado di portare il numero di ordini per pagina a 20 dalla pagina 2 quando sono presenti 11 ordini. Inoltre, se ci sono più ordini di quanti ne sia configurato per essere visualizzato per pagina, quando si passa all’ultima pagina con gli ordini, la modifica del numero di ordini mostrati per pagina genera il messaggio di errore: *Non hai effettuato alcun ordine*. Questo problema verrà risolto in Adobe Commerce 2.4.1.

## Prodotti e versioni interessati

* Adobe Commerce on-premise 2.4.0
* Adobe Commerce sull’infrastruttura cloud 2.4.0

## Problema

<u>Prerequisiti</u>

* Adobe Commerce 2.4.0 è installato.
* Crea almeno una categoria e un prodotto semplice.

<u>Passaggi da riprodurre</u>

1. Crea 11 ordini con i prodotti.
1. Vai a **Il mio account**.
1. Vai a **I miei ordini**.
1. Fare clic sulla seconda pagina per visualizzare l&#39;undicesimo ordine nella griglia degli ordini.
1. Seleziona **Show = 20 per pagina** dal menu a discesa.

<u>Risultato previsto</u>

Tutti gli 11 ordini vengono visualizzati sulla prima pagina, come previsto.

<u>Risultato effettivo</u>

Il *Non hai effettuato alcun ordine* viene visualizzato un messaggio di errore.

## Soluzione alternativa

La soluzione consiste nel far riaprire l&#39;acquirente **I miei ordini** e quindi l&#39;elenco degli ordini verrà visualizzato correttamente. Il problema verrà risolto nella prossima versione, Adobe Commerce 2.4.1, il cui rilascio è pianificato per il quarto trimestre del 2020.

## Letture correlate nella knowledge base di supporto

* [Problema noto di Adobe Commerce 2.4.0: l’aggiornamento delle attività del cliente non funziona](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0 Problema noto: visualizzazione dei dati dei messaggi non elaborati in Storefront](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Problema noto di Adobe Commerce 2.4.0: l’esportazione delle aliquote fiscali non funziona](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [L’amministratore B2B di Adobe Commerce 2.4.0 non può aggiungere un prodotto configurabile all’offerta](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
