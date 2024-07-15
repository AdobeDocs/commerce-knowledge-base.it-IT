---
title: Richiesta rifiutata gateway PayPal - problema fattura duplicata
description: Questo articolo fornisce una correzione per la richiesta rifiutata del gateway PayPal - emissione di fattura duplicata.
exl-id: b6c4ede1-97a5-4db3-9b05-ab979cf809b3
feature: Invoices, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# Richiesta rifiutata gateway PayPal - problema fattura duplicata

Questo articolo fornisce una correzione per la richiesta rifiutata del gateway PayPal - emissione di fattura duplicata.

Quando si sottomette il pagamento, i clienti potrebbero visualizzare un errore per una fattura duplicata:

>Il gateway PayPal ha rifiutato la richiesta. Il pagamento per questo ID fattura è già stato eseguito (\#10412: fattura duplicata)

Il problema si verifica quando le fatture con gli stessi ID vengono inviate a PayPal più volte.

Per risolvere il problema, consenti più pagamenti per ID fattura nelle Preferenze di ricezione pagamento di PayPal. Quando viene modificato, PayPal accetta pagamenti senza messaggi di errore, anche per le fatture con ID duplicati.

## Versioni interessate

* Adobe Commerce on-premise, tutte le versioni
* Adobe Commerce su infrastruttura cloud, tutte le versioni

## Problema

Quando si invia il pagamento, i clienti visualizzano il messaggio di errore:

```
... main.CRITICAL: Exception message: PayPal gateway has rejected request. Payment has already been made for this InvoiceID (#10412: Duplicate invoice).
```

PayPal non può elaborare il pagamento e completare l&#39;ordine.

## Causa

Il messaggio di errore viene visualizzato quando le fatture con lo stesso ID vengono inviate a PayPal più volte.

Ciò può verificarsi quando si utilizzano le stesse credenziali in diversi siti di Adobe Commerce (anche negli ambienti locali e di staging). Di seguito sono riportati alcuni scenari particolari:

* Più magazzini inviano le fatture a PayPal e utilizzano gli stessi ID fattura
* Un nuovo archivio invia una fattura con un ID precedentemente inviato da un vecchio archivio

Per impostazione predefinita, PayPal non consente di elaborare due volte la stessa fattura.

## Soluzione

Modifica il tuo profilo PayPal per consentire più pagamenti per ID fattura. Devi apportare queste modifiche tramite PayPal.

1. Accedi al tuo account all&#39;indirizzo [https://www.paypal.com](https://www.paypal.com/).
1. Fai clic su **Profilo** > **Profilo e impostazioni** (angolo superiore destro).
1. Vai a **I miei strumenti di vendita**.
1. Passa a **Pagamento e gestione dei rischi** > **Blocca pagamenti** e fai clic su **Aggiorna**.
1. **Preferenze di vendita**, fai clic su **Preferenze di ricezione pagamento**.
1. In **Blocca pagamenti accidentali**, scegliere **No, consenti più pagamenti per ID fattura**.    ![paypal_allow_multiple_payments_per_invo_id.png](assets/paypal_allow_multiple_payments_per_invoice_id.png)
1. Scorri verso il basso e fai clic su **Salva**.

## Ulteriori informazioni

* [Blocca pagamenti accidentali](https://developer.paypal.com/docs/admin/setup-account/#block-accidental-payments) nei documenti per sviluppatori PayPal.
* Pagamenti PayPal nella nostra guida utente:
   * [Pagamento PayPal Express](/docs/commerce-admin/stores-sales/payments/paypal/paypal-express-checkout.html)
   * [Altre soluzioni PayPal](/docs/commerce-admin/stores-sales/payments/paypal/paypal.html)
* Nella documentazione per gli sviluppatori:
   * [Impostare i metodi di pagamento PayPal per Adobe Commerce su infrastruttura cloud](/docs/commerce-cloud-service/user-guide/configure-store/paypal.html)
   * [Integrazioni pagamenti](https://developer.adobe.com/commerce/php/development/payments-integrations/)
