---
title: "Adobe Commerce 2.4.4: impossibile creare fatture parziali"
description: Questo articolo fornisce un hotfix per il problema che impedisce agli utenti di creare fatture parziali quando si utilizzano Apple Pay o Google Pay tramite Braintree come metodi di pagamento.
exl-id: bf78cc07-9dc7-4eb8-bfdf-57ea5131effb
feature: Invoices, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# Adobe Commerce 2.4.4: impossibile creare fatture parziali

Questo articolo fornisce un hotfix per il problema che impedisce agli utenti di creare fatture parziali quando si utilizzano Apple Pay o Google Pay tramite Braintree come metodi di pagamento.

## Prodotti e versioni interessati

Adobe Commerce (tutti i metodi di implementazione) 2.4.4

## Problema

Quando si utilizza Apple Pay o Google Pay come metodi di pagamento, gli utenti ricevono l’errore &quot;*Il comando ‘vault_capture’ non esiste. Verifica il comando e riprova.*&quot; durante la creazione di fatture parziali.

<u>Passaggi da riprodurre</u>:

1. Apri il tuo sito web Adobe Commerce.
1. Aggiungere un prodotto semplice al carrello (qtà 2).
1. Scegli **Apple Pay** o **Google Pay** come metodo di pagamento dal carrello.
1. Effettua l’ordine.
1. Apri i dettagli dell’ordine dal back-end.
1. Creare una fattura parziale.
1. Crea un&#39;altra fattura per l&#39;importo rimanente.

<u>Risultati previsti</u>:

Vengono create fatture parziali.

<u>Risultati effettivi</u>:

Viene creata la prima fattura parziale. Durante la creazione della seconda fattura parziale, gli utenti ricevono il seguente errore: *Il comando ‘vault_capture’ non esiste. Verifica il comando e riprova*.

## Causa

Adobe Commerce salva i dettagli della carta di credito nel vault per creare fatture parziali. Attualmente, non è disponibile alcuna funzionalità per il vaulting di Apple Pay e Google Pay.

## Soluzione

Per risolvere il problema, applica la seguente patch:

[Braintree_disabled_partial_capture_for_applepay_googlepay.zip](assets/braintree-disabled-partial-capture-for-applepay-googlepay.zip)

## Come applicare il cerotto

Consulta [Come applicare una patch del compositore fornita dall&#39;Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) per istruzioni.
