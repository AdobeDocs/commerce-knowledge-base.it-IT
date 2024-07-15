---
title: "Adobe Commerce 2.4.0, 2.4.1: Abilita fattura parziale Braintree Venmo"
description: Questo articolo descrive un problema noto di Adobe Commerce 2.4.0 e 2.4.1, in cui la fattura parziale non è disponibile per gli ordini effettuati utilizzando la Braintree tramite Venmo.
exl-id: ef6c8aa4-a2a7-4e07-a957-23173017baf2
feature: Invoices, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---

# Adobe Commerce 2.4.0, 2.4.1: Abilitare la fattura parziale Braintree Venmo

Questo articolo descrive un problema noto di Adobe Commerce 2.4.0 e 2.4.1, in cui la fattura parziale non è disponibile per gli ordini effettuati utilizzando la Braintree tramite Venmo.

## Prodotti e versioni interessati

* Adobe Commerce on-premise 2.4.0 e 2.4.1
* Adobe Commerce sull’infrastruttura cloud 2.4.0 e 2.4.1

## Problema

<u>Prerequisiti:</u>

Nella configurazione del metodo di pagamento Braintree, impostare **Abilita Venmo tramite Braintree** = *Sì* con **Azione di pagamento** = *Autorizzazione*; **Abilita Vault per pagamenti con carta** = *No*.

<u>Passaggi da riprodurre:</u>

1. Crea un ordine per due o più prodotti, utilizzando Venmo (Braintree) come metodo di pagamento.
1. Apri l’ordine in Amministrazione Commerce.
1. Crea una fattura per uno dei prodotti ordinati.
1. Provare a creare una fattura per i prodotti ordinati rimanenti.

<u>Risultato previsto:</u>

Fattura creata.

<u>Risultato effettivo:</u>

Viene visualizzato il seguente messaggio di errore: *Il comando &quot;vault\_capture&quot; non esiste. Verificare il comando e riprovare.*

## Soluzione alternativa

Acquisire l&#39;intero importo durante la creazione di fatture per ordini effettuati utilizzando Braintree tramite Venmo.
