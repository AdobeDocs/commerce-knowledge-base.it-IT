---
title: Aggiornamento indirizzo e-mail del messaggio di convalida degli indirizzi verticali di Adobe Commerce 2.4.1
description: Questo articolo descrive un problema noto di Adobe Commerce 2.4.1 in cui la convalida degli indirizzi Vertex non funziona durante la fase di pagamento quando viene utilizzato un indirizzo di spedizione diverso dall’indirizzo di fatturazione. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.2.
exl-id: c2abeb96-e837-4d16-92dd-82fea5661dd9
feature: Shipping/Delivery
role: Developer
source-git-commit: ce377064efabaf09d3856da7c6c5c742a9fdcc2f
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# Aggiornamento indirizzo e-mail del messaggio di convalida degli indirizzi verticali di Adobe Commerce 2.4.1

Questo articolo descrive un problema noto di Adobe Commerce 2.4.1 in cui la convalida degli indirizzi Vertex non funziona durante la fase di pagamento quando viene utilizzato un indirizzo di spedizione diverso dall’indirizzo di fatturazione. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.2.

## Prodotti e versioni interessati

* Adobe Commerce on-premise 2.4.1 con integrazione Vertex abilitata
* Adobe Commerce su infrastruttura cloud 2.4.1 con integrazione Vertex abilitata

## Problema


<u>Passaggi da riprodurre:</u>

1. Crea un account e accedi.
1. Aggiungere un elemento al carrello facendo clic su **Aggiungi al carrello**. Fai clic sull&#39;icona del carrello, quindi fai clic su **Procedi all&#39;estrazione**.
1. Immettere un indirizzo valido nel campo **Indirizzo di spedizione**.
1. Selezionare una delle opzioni in **Metodi di spedizione**. Quindi fare clic su **Avanti**.
1. Se la convalida degli indirizzi suggerisce informazioni sull&#39;indirizzo diverse, fare clic su **Aggiorna indirizzo** e su **Avanti**.
1. Deseleziona **La casella di controllo Il mio indirizzo di fatturazione e di spedizione è uguale**.

<u>Primo scenario:</u>

Segui i [sei passaggi precedenti](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md#first_sixth) e quindi:

1. Immettere un nuovo indirizzo di fatturazione valido.
1. Fai clic sul pulsante **Aggiorna**. Il messaggio/suggerimento verrà visualizzato come segue: *Indirizzo non valido.* Seguirà un suggerimento di indirizzo come: *Codice postale: XXXXX- XXXX Via: XXX Via XXX*
1. Fai clic sul pulsante **Aggiorna** (non fare clic sul pulsante **Aggiorna indirizzo** del suggerimento per gli indirizzi verticali).
1. Fai clic sul pulsante **Modifica** dell&#39;indirizzo di fatturazione aggiornato.
1. Seleziona l’indirizzo dal menu a discesa dell’indirizzo.
1. Fai clic sul pulsante **Aggiorna**.

<u>Risultato previsto:</u>

Il messaggio di convalida/suggerimento precedente viene rimosso.

<u>Risultato effettivo:</u>

Messaggio/suggerimento di convalida *&quot;Indirizzo non valido Codice postale: XXXXX-XXXX Via: XXX Via XXX Città XXX&quot;* Il messaggio è **NOT** rimosso. Lo stesso problema si verifica se si immette un indirizzo non valido nel modulo.

<u>Secondo scenario:</u>

Segui i [sei passaggi precedenti](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md#first_sixth) e quindi:

1. Compila il modulo dell’indirizzo con un indirizzo valido.
1. Fai clic sul pulsante **Aggiorna**. Il messaggio/suggerimento verrà visualizzato come segue: *Indirizzo non valido.* Seguirà un suggerimento di indirizzo come: *Codice postale: XXXXX-XXXX Via: XXX Via XXX*.
1. Fai clic sul pulsante **Aggiorna** (non fare clic sul pulsante **Aggiorna indirizzo** del suggerimento di indirizzo del vertice).
1. Controlla che l&#39;elenco a discesa ***Il mio indirizzo di fatturazione e di spedizione sia lo stesso***.

<u>Risultato previsto:</u>

Il messaggio di convalida/suggerimento precedente viene rimosso.

<u>Risultato effettivo:</u>

Messaggio/suggerimento di convalida *&quot;Non è stato trovato un indirizzo valido Codice postale: XXXXX-XXXX Via XXX Via XXX Città XXX&quot;* Il messaggio è **NOT** rimosso. Lo stesso problema si verifica se si immette un indirizzo non valido nel modulo.

## Lettura correlata nella knowledge base di supporto:

[Problema noto di Adobe Commerce 2.3.6, 2.4.0-p1 e 2.4.1: impossibile accedere a dotdigital quando l’account è abilitato](/help/troubleshooting/miscellaneous/magento-2-3-6-2-4-0-p1-2-4-1-known-issue-dotdigital-login.md)
