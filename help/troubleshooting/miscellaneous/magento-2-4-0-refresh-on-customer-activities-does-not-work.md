---
title: "Adobe Commerce 2.4.0: l’aggiornamento delle attività del cliente non funziona"
description: Questo articolo fornisce una soluzione per il problema noto di Adobe Commerce 2.4.0 quando un utente amministratore crea un ordine per un cliente e i pulsanti di aggiornamento nel pannello laterale Attività del cliente non funzionano.
exl-id: 50048e9f-6009-4db5-ae4a-c35a84cec265
feature: Configuration
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '415'
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
1. Fai clic su **Crea nuovo ordine** pulsante.
1. Seleziona il cliente creato.
1. Vai alla vetrina come cliente creato.
1. Vai a **Prodotto** pagina. Fai clic su **Aggiorna** pulsante sulla **Prodotti visualizzati di recente** sezione di **Attività del cliente**.
1. Torna alla vetrina.
1. Effettua un ordine utilizzando i prodotti creati.
1. Torna a **Pannello di amministrazione** e fai clic su **Aggiorna** pulsante della **Ultimi articoli ordinati** sezione di **Attività del cliente**.
1. Torna alla vetrina. Aggiungi il prodotto creato al **Elenco di confronto**.
1. Torna a **Pannello di amministrazione**. Fai clic su **Aggiorna** pulsante della **Prodotti in Elenco di confronto** sezione di **Attività del cliente**.
1. Torna alla vetrina.
1. Rimuovi il prodotto creato da **Elenco di confronto**.
1. Torna a **Pannello di amministrazione**.
1. Fai clic su **Aggiorna** pulsante della **Prodotti confrontati di recente** sezione di **Attività del cliente**.
1. Torna alla vetrina.

<u>Risultati previsti</u>:

Il nome del prodotto deve essere visualizzato nel **Prodotti visualizzati di recente**, **Ultimi articoli ordinati**, **Prodotti in Elenco di confronto**, e **Prodotti confrontati di recente** sezione.

<u>Risultati effettivi</u>:

La pagina viene scorsa verso l’alto ogni volta che **Aggiorna** clic sul pulsante. Il nome del prodotto non viene visualizzato nella sezione corretta.

## Soluzione

L’utente amministratore può aggiornare una soluzione alternativa **Attività del cliente** facendo clic su **Aggiorna modifiche** nella parte inferiore della barra laterale. Il problema è pianificato per essere risolto nella patch di Adobe Commerce 2.4.1.

![mceclip0.png](assets/mceclip0.png)

## Lettura correlata

* [Problema noto di Adobe Commerce 2.4.0: i metodi di pagamento Braintree non vengono visualizzati nel checkout di più indirizzi](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problema noto nella creazione di etichette di spedizione in Adobe Commerce 2.4.0](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
* [Problema noto di Adobe Commerce 2.4.0: visualizzazione dei dati dei messaggi non elaborati nella vetrina](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Problema noto di Adobe Commerce 2.4.0: l’esportazione delle aliquote fiscali non funziona](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Problema noto di Adobe Commerce 2.4.0: il pulsante &quot;Aggiungi selezioni al carrello&quot; non funziona](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
