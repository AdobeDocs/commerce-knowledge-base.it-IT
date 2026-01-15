---
title: L’amministratore B2B di Adobe Commerce 2.4.0 non può aggiungere un prodotto configurabile all’offerta
description: Questo articolo parla di un problema noto in Commerce Admin quando si gestisce un preventivo B2B, non è possibile aggiungere al preventivo un prodotto configurabile tramite **SKU**. Quando si fa clic sul pulsante **Aggiungi a preventivo**, la pagina di modifica **Preventivo** si blocca e non è possibile configurare il prodotto e salvare le modifiche. Questo problema si verifica anche in Admin quando si aggiunge un prodotto tramite **SKU** a un ordine o quando si aggiunge un prodotto tramite **SKU** in **Advanced Checkout** (**Admin** &gt; **Customers** &gt; **All Customers** &gt; **Customer Edit** &gt; **Manage Shopping Cart**). Questo problema verrà risolto in una patch per Adobe Commerce 2.4.1.
exl-id: 73f7231b-b496-4250-b9e2-29427c772d56
feature: Admin Workspace, B2B, Catalog Management, Configuration, Products, Quotes
role: Developer
source-git-commit: 05297c82b292b8ccc88018c58e991bd3a32d6ffa
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 0%

---

# L’amministratore B2B di Adobe Commerce 2.4.0 non può aggiungere un prodotto configurabile all’offerta

In questo articolo viene illustrato un problema noto in Commerce Admin durante la gestione di un preventivo B2B. Non è possibile aggiungere al preventivo un prodotto configurabile con **SKU**. Quando si fa clic sul pulsante **Aggiungi a preventivo**, la pagina di modifica **Preventivo** è bloccata e non è possibile configurare il prodotto e salvare le modifiche. Questo problema si verifica anche in Amministratore quando si aggiunge un prodotto da **SKU** a un ordine o quando si aggiunge un prodotto da **SKU** in **Pagamento avanzato** (**Amministratore** > **Clienti** > **Tutti i clienti** > **Modifica cliente** > **Gestisci carrello**). Questo problema verrà risolto in una patch per Adobe Commerce 2.4.1.

## Prodotti e versioni interessati

* Adobe Commerce on-premise 2.4.0
* Adobe Commerce sull’infrastruttura cloud 2.4.0

## Problema

<u>Condizioni preliminari</u>

* Adobe Commerce 2.4.0 è installato.
* B2B è installato.
* Impostare le funzionalità B2B su **Abilita società =** *Sì* , **Abilita catalogo condiviso =** *No* e **Abilita preventivo B2B =** *Sì*.
* Crea un account cliente.
* Crea un account aziendale con il cliente creato in precedenza come amministratore della società.
* Creare un prodotto semplice (esempio: nome e **SKU** = TEST SIMPLE 1) non assegnato a **Default (General)**.
* Chiedi all’amministratore dell’azienda di richiedere un preventivo utilizzando il prodotto semplice creato in precedenza (esempio: TEST SIMPLE 1).

<u>Passaggi da riprodurre</u>

1. Passa al pannello di amministrazione di Commerce.
1. Vai a **Vendite > Preventivi**.
1. Apri il **preventivo**.
1. Fai clic sul pulsante **Aggiungi prodotto per SKU**.
1. Immetti lo **SKU** di un altro prodotto (esempio: TEST SIMPLE 2) nel campo di input **Enter SKU**.
1. Immettere una quantità valida nel campo di input **Qtà**.
1. Fare clic sul pulsante **Aggiungi al preventivo**.

<u>Risultati previsti</u>

* La griglia **Prodotti non aggiunti al preventivo**, contenente il nome e **SKU** del prodotto creato, viene visualizzata come previsto.
* Dopo aver configurato il prodotto, l&#39;amministratore è in grado di aggiungerlo al **preventivo** facendo clic sul pulsante **Aggiungi prodotti al preventivo**, come previsto.

<u>Risultati effettivi</u>

* La griglia **Prodotti non aggiunti al preventivo**, contenente il nome e **SKU** del prodotto creato, non viene visualizzata.
* Caricamento della pagina **Offerta** bloccato.

## Consiglio

Attualmente, non esiste una soluzione alternativa per questo problema con la modifica dei preventivi B2B, ma per la gestione degli ordini e del carrello acquisti è possibile selezionare i prodotti dall&#39;**elenco prodotti** invece di aggiungerli per **SKU**. Una patch per risolvere il problema sarà disponibile per Adobe Commerce 2.4.1, il cui rilascio è pianificato per il quarto trimestre del 2020.

