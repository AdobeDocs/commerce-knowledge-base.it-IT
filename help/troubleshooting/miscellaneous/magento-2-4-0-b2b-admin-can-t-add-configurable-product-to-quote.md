---
title: L’amministratore B2B di Adobe Commerce 2.4.0 non può aggiungere un prodotto configurabile all’offerta
description: Questo articolo parla di un problema noto in Commerce Admin quando si gestisce un preventivo B2B, non è possibile aggiungere al preventivo un prodotto configurabile tramite **SKU**. Quando si fa clic sul pulsante **Aggiungi a preventivo**, la pagina di modifica **Preventivo** si blocca e non è possibile configurare il prodotto e salvare le modifiche. Questo problema si verifica anche in Admin quando si aggiunge un prodotto tramite **SKU** a un ordine o quando si aggiunge un prodotto tramite **SKU** in **Advanced Checkout** (**Admin** &gt; **Customers** &gt; **All Customers** &gt; **Customer Edit** &gt; **Manage Shopping Cart**). Questo problema verrà risolto in una patch per Adobe Commerce 2.4.1.
exl-id: 73f7231b-b496-4250-b9e2-29427c772d56
feature: Admin Workspace, B2B, Catalog Management, Configuration, Products, Quotes
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 0%

---

# L’amministratore B2B di Adobe Commerce 2.4.0 non può aggiungere un prodotto configurabile all’offerta

Questo articolo parla di un problema noto in Commerce Admin quando si gestisce un preventivo B2B, non è possibile aggiungere un prodotto configurabile tramite **SKU** al preventivo. Quando si fa clic su **Aggiungi al preventivo** pulsante, il pulsante **Citazione** il caricamento della pagina di modifica è bloccato e non è possibile configurare il prodotto e salvare le modifiche. Questo problema si verifica anche in Amministratore quando si aggiunge un prodotto tramite **SKU** a un ordine o aggiungendo un prodotto tramite **SKU** in **Pagamento avanzato** (**Amministratore** > **Clienti** > **Tutti i clienti** > **Modifica cliente** > **Gestisci carrello**). Questo problema verrà risolto in una patch per Adobe Commerce 2.4.1.

## Prodotti e versioni interessati

* Adobe Commerce on-premise 2.4.0
* Adobe Commerce sull’infrastruttura cloud 2.4.0

## Problema

<u>Precondizioni</u>

* Adobe Commerce 2.4.0 è installato.
* B2B è installato.
* Impostare le funzioni B2B su **Abilita società =**  *Sì* , **Abilita catalogo condiviso =**  *No* , e **Abilita offerta B2B =**  *Sì*.
* Crea un account cliente.
* Crea un account aziendale con il cliente creato in precedenza come amministratore della società.
* Creare un prodotto semplice (esempio: nome e **SKU** = TEST SIMPLE 1) non assegnato a **Predefinito (generale)**.
* Chiedi all’amministratore dell’azienda di richiedere un preventivo utilizzando il prodotto semplice creato in precedenza (esempio: TEST SIMPLE 1).

<u>Passaggi da riprodurre</u>

1. Passa al pannello di amministrazione di Commerce.
1. Vai a **Vendite > Offerte**.
1. Apri **Citazione**.
1. Fai clic su **Aggiungi prodotto per SKU** pulsante.
1. Inserisci il **SKU** di un altro prodotto (ad esempio: TEST SIMPLE 2) in **Inserisci SKU** campo di input.
1. Immettere una quantità valida nel campo **Qtà** campo di input.
1. Fai clic su **Aggiungi al preventivo** pulsante.

<u>Risultati previsti</u>

* Il **Prodotti non aggiunti al preventivo** griglia, contenente il nome e **SKU** del prodotto creato, viene visualizzato come previsto.
* Una volta configurato il prodotto, l’Amministratore può aggiungerlo al **Citazione** facendo clic su **Aggiungi prodotti all&#39;offerta** come previsto.

<u>Risultati effettivi</u>

* Il **Prodotti non aggiunti al preventivo** griglia, contenente il nome e **SKU** del prodotto creato, non viene visualizzato.
* Il **Citazione** caricamento della pagina bloccato.

## Consiglio

Attualmente, non esiste una soluzione alternativa per questo problema con la modifica dei preventivi B2B, ma per la gestione degli ordini e del carrello acquisti è possibile selezionare i prodotti dalla sezione **Elenco prodotti** invece di aggiungerli tramite **SKU**. Una patch per risolvere il problema sarà disponibile per Adobe Commerce 2.4.1, il cui rilascio è pianificato per il quarto trimestre del 2020.

## Lettura correlata

* [Problema noto di Adobe Commerce 2.4.0: l’aggiornamento delle attività del cliente non funziona](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0 Problema noto: visualizzazione dei dati dei messaggi non elaborati in Storefront](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Problema noto di Adobe Commerce 2.4.0: l’esportazione delle aliquote fiscali non funziona](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0 problema noto: errore di visualizzazione degli ordini](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
