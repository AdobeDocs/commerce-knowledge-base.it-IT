---
title: 'Adobe Commerce 2.4.0: l’aggiornamento delle attività del cliente non funziona'
description: Questo articolo fornisce una soluzione per il problema noto di Adobe Commerce 2.4.0 quando un utente amministratore crea un ordine per un cliente e i pulsanti di aggiornamento nel pannello laterale Attività del cliente non funzionano.
exl-id: 50048e9f-6009-4db5-ae4a-c35a84cec265
feature: Configuration
role: Developer
source-git-commit: a1046621259ea49eab74cd6ba3bba550e0c70283
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: l’aggiornamento delle attività del cliente non funziona

Questo articolo fornisce una soluzione per il problema noto di Adobe Commerce 2.4.0 quando un utente amministratore crea un ordine per un cliente e i pulsanti di aggiornamento nel pannello laterale Attività del cliente non funzionano.

## Prodotti e versioni interessati

* Adobe Commerce on-premise 2.4.0
* Adobe Commerce sull’infrastruttura cloud 2.4.0

## Problema

<u>Passaggi da riprodurre</u>:

1. Vai a **Pannello di amministrazione** > **Vendite** > **Ordini**.
1. Fai clic sul pulsante **Crea nuovo ordine**.
1. Seleziona il cliente creato.
1. Vai alla vetrina come cliente creato.
1. Vai alla pagina **Prodotto**. Fai clic sul pulsante **Aggiorna** nella sezione **Prodotti visualizzati di recente** delle **Attività del cliente**.
1. Torna alla vetrina.
1. Effettua un ordine utilizzando i prodotti creati.
1. Torna al **Pannello di amministrazione** e fai clic sul pulsante **Aggiorna** della sezione **Ultimi elementi ordinati** delle **Attività del cliente**.
1. Torna alla vetrina. Aggiungere il prodotto creato all&#39;**Elenco di confronto**.
1. Torna al **Pannello di amministrazione**. Fai clic sul pulsante **Aggiorna** della sezione **Prodotti nell&#39;elenco di confronto** delle **Attività del cliente**.
1. Torna alla vetrina.
1. Rimuovere il prodotto creato dall&#39;**elenco di confronto**.
1. Torna al **Pannello di amministrazione**.
1. Fai clic sul pulsante **Aggiorna** nella sezione **Prodotti confrontati di recente** delle **Attività del cliente**.
1. Torna alla vetrina.

<u>Risultati previsti</u>:

Il nome del prodotto deve essere visualizzato nella sezione **Prodotti visualizzati di recente**, **Ultimi articoli ordinati**, **Prodotti in elenco confronto** e **Prodotti confrontati di recente**.

<u>Risultati effettivi</u>:

Viene eseguito lo scorrimento della pagina ogni volta che si fa clic su un pulsante **Aggiorna**. Il nome del prodotto non viene visualizzato nella sezione corretta.

## Soluzione

Una soluzione alternativa consiste nel fatto che l&#39;utente amministratore può aggiornare **le attività del cliente** facendo clic sul pulsante **Aggiorna modifiche** nella parte inferiore della barra laterale. Il problema è pianificato per essere risolto nella patch di Adobe Commerce 2.4.1.

![mceclip0.png](assets/mceclip0.png)

## Lettura correlata

* [Problema noto di Adobe Commerce 2.4.0: i metodi di pagamento Braintree non vengono visualizzati nel checkout di più indirizzi](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problema noto di Adobe Commerce 2.4.0: visualizzazione dei dati dei messaggi non elaborati nella vetrina](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Problema noto di Adobe Commerce 2.4.0: l’esportazione delle aliquote fiscali non funziona](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problema noto di Adobe Commerce 2.4.0: il pulsante &quot;Aggiungi selezioni al carrello&quot; non funziona](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
