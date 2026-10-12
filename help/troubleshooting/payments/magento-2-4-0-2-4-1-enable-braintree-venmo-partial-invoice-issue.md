---
title: 'Adobe Commerce 2.4.0, 2.4.1: Abilita fattura parziale Braintree Venmo'
description: Questo articolo descrive un problema noto di Adobe Commerce 2.4.0 e 2.4.1, in cui la fattura parziale non è disponibile per gli ordini effettuati utilizzando Braintree tramite Venmo.
exl-id: ef6c8aa4-a2a7-4e07-a957-23173017baf2
feature: Invoices, Orders, Payments
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 591c578b-908e-5b79-a9d3-931dfe60c24c
    internal-label: Invoices
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%
---
# Adobe Commerce 2.4.0, 2.4.1: Abilita fattura parziale Braintree Venmo

Questo articolo descrive un problema noto di Adobe Commerce 2.4.0 e 2.4.1, in cui la fattura parziale non è disponibile per gli ordini effettuati utilizzando Braintree tramite Venmo.

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

Acquisisci l’intero importo durante la creazione di fatture per ordini effettuati utilizzando Braintree tramite Venmo.
