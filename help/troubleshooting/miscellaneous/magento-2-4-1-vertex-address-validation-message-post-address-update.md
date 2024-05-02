---
title: Aggiornamento indirizzo e-mail del messaggio di convalida degli indirizzi verticali di Adobe Commerce 2.4.1
description: Questo articolo descrive un problema noto di Adobe Commerce 2.4.1 in cui la convalida degli indirizzi Vertex non funziona durante la fase di pagamento quando viene utilizzato un indirizzo di spedizione diverso dall’indirizzo di fatturazione. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.2.
exl-id: c2abeb96-e837-4d16-92dd-82fea5661dd9
feature: Shipping/Delivery
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 0%

---

# Aggiornamento indirizzo e-mail del messaggio di convalida degli indirizzi verticali di Adobe Commerce 2.4.1

Questo articolo descrive un problema noto di Adobe Commerce 2.4.1 in cui la convalida degli indirizzi Vertex non funziona durante la fase di pagamento quando viene utilizzato un indirizzo di spedizione diverso dall’indirizzo di fatturazione. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.2.

## Prodotti e versioni interessati

* Adobe Commerce on-premise 2.4.1 con integrazione Vertex abilitata
* Adobe Commerce su infrastruttura cloud 2.4.1 con integrazione Vertex abilitata

## Problema

Prerequisiti:

Abilita **Pulizia degli indirizzi verticali**. Per i passaggi, consulta [Configurazione della pulizia degli indirizzi di Storefront](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/vertex-address-cleansing-different-addresses-not-allowed.html) nella guida utente.

<u>Passaggi da riprodurre:</u>

1. Crea un account e accedi.
1. Aggiungi un articolo al carrello facendo clic su **Aggiungi al carrello**. Fai clic sull’icona del carrello, quindi fai clic su **Procedi all&#39;estrazione**.
1. Immetti un indirizzo valido in **Indirizzo di spedizione** campo.
1. Seleziona una delle opzioni in **Metodi di spedizione**. Quindi fai clic su **Successivo**.
1. Se la convalida degli indirizzi suggerisce informazioni diverse sull&#39;indirizzo, fare clic su **Aggiorna indirizzo** e fai clic su **Successivo**.
1. Deseleziona la **Il mio indirizzo di fatturazione e spedizione è lo stesso** casella di controllo.

<u>Primo scenario:</u>

Segui le [oltre sei passaggi](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md#first_sixth) e quindi:

1. Immettere un nuovo indirizzo di fatturazione valido.
1. Fai clic sul pulsante **Aggiorna** pulsante. Il messaggio/suggerimento verrà visualizzato come segue: *Indirizzo non valido.* Seguirà un suggerimento di indirizzo come: *Codice postale : XXXXX- XXXX Via : XXX Via XXX*
1. Fai clic sul pulsante **Aggiorna** (non fare clic sul pulsante **Aggiorna indirizzo** suggerimento di indirizzi verticali).
1. Fai clic sul pulsante **Modifica** pulsante dell’indirizzo di fatturazione aggiornato.
1. Seleziona l’indirizzo dal menu a discesa dell’indirizzo.
1. Fai clic sul pulsante **Aggiorna** pulsante.

<u>Risultato previsto:</u>

Il messaggio di convalida/suggerimento precedente viene rimosso.

<u>Risultato effettivo:</u>

Messaggio/suggerimento di convalida *&quot;Indirizzo non valido Codice postale : XXXXX-XXXX Via : XXX Via XXX Città XXX&quot;* il messaggio è **NOT** è stato rimosso. Lo stesso problema si verifica se si immette un indirizzo non valido nel modulo.

<u>Secondo scenario:</u>

Segui le [oltre sei passaggi](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md#first_sixth) e quindi:

1. Compila il modulo dell’indirizzo con un indirizzo valido.
1. Fai clic sul pulsante **Aggiorna** pulsante. Il messaggio/suggerimento verrà visualizzato come segue: *Indirizzo non valido.* Seguirà un suggerimento di indirizzo come: *Codice di avviamento postale: XXXXX-XXXX Via: XXX Via XXX*.
1. Fai clic sul pulsante **Aggiorna** (non fare clic sul pulsante **Aggiorna indirizzo** pulsante di suggerimento dell&#39;indirizzo del vertice).
1. Controlla la ***Il mio indirizzo di fatturazione e spedizione è lo stesso*** a discesa.

<u>Risultato previsto:</u>

Il messaggio di convalida/suggerimento precedente viene rimosso.

<u>Risultato effettivo:</u>

Messaggio/suggerimento di convalida *&quot;Indirizzo non valido Codice postale: XXXXX-XXXX Street XXX City street XXX&quot;* il messaggio è **NOT** è stato rimosso. Lo stesso problema si verifica se si immette un indirizzo non valido nel modulo.

## Lettura correlata nella knowledge base di supporto:

[Problema noto di Adobe Commerce 2.3.6, 2.4.0-p1 e 2.4.1: impossibile accedere a dotdigital quando l’account è abilitato](/help/troubleshooting/miscellaneous/magento-2-3-6-2-4-0-p1-2-4-1-known-issue-dotdigital-login.md)
