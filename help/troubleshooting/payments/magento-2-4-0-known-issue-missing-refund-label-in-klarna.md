---
title: 'Adobe Commerce 2.4.0 problema noto: etichetta "Refund" mancante in Klarna'
description: Questo articolo fornisce una soluzione alternativa per un problema noto in Admin (Amministrazione) relativo a un’etichetta **Refund** mancante in Klarna VBE (estensione bundled per fornitori). Quando nel portale Klarna si esegue un rimborso, l’etichetta **Rimborso** non viene visualizzata accanto al prodotto nel pacchetto rimborsato.
exl-id: f08039b2-7f8b-481e-8ec8-1659e227744f
feature: B2B, Orders, Payments
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%
---
# Adobe Commerce 2.4.0 problema noto: etichetta &quot;Refund&quot; mancante in Klarna

Questo articolo fornisce una soluzione alternativa per un problema noto in Admin relativo a un&#39;etichetta **Rimborso** mancante in Klarna VBE (Vendor Bundled Extension). Quando nel portale Klarna si esegue un rimborso, l&#39;etichetta **Rimborso** non viene visualizzata accanto al prodotto nel pacchetto rimborsato.

## Prodotti e versioni interessati

* Adobe Commerce on-premise 2.4.0
* Adobe Commerce sull’infrastruttura cloud 2.4.0

## Problema

<u>Prerequisiti:</u>

* Klarna attivato.
* Viene creato un prodotto in bundle.

<u>Passaggi da riprodurre</u>

1. Vai a Adobe Commerce frontend e aggiungi un prodotto in bundle al **carrello**.
1. Passa a pagamento.
1. Immettere le informazioni del consumatore nell&#39;estrazione e fare clic su **Avanti**.
1. Seleziona **opzione KP** e fai clic su **Inserisci ordine**.
1. Vai a **Amministratore** > **Vendite** > **Ordini**.
1. Apri l’ordine.
1. Crea fattura per prodotto.
1. Vai a **Fatture** > **Seleziona fattura** > Fai clic su **Nota di credito** > Fai clic su **Rimborso** (non su **Rimborso offline**).
1. Vai al portale Klarna.
1. Apri l’ordine.
1. L&#39;etichetta **Rimborso** è presente.

<u>Risultato previsto</u>

Sul portale Klarna, l&#39;etichetta **Rimborso** viene visualizzata accanto al prodotto rimborsato.

<u>Risultato effettivo</u>

Sul portale Klarna, l&#39;etichetta **Rimborso** non viene visualizzata accanto al prodotto rimborsato.

## Soluzione alternativa

La soluzione per questo problema consiste nell&#39;ignorare l&#39;etichetta **Rimborso** mancante nel portale Klarna per i prodotti in bundle rimborsati. Il rimborso è stato effettuato anche se l&#39;etichetta **Rimborso** non è stata visualizzata. Il problema dovrebbe essere risolto in Adobe Commerce 2.4.1, il cui rilascio è pianificato per il quarto trimestre del 2020.

## Letture correlate nella knowledge base di supporto:

* [Problema noto di Adobe Commerce 2.4.0: i metodi di pagamento di Braintree non vengono visualizzati nell’estrazione di più indirizzi](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Problema noto di Adobe Commerce 2.4.0: messaggio di errore durante la selezione del metodo di pagamento locale visualizzato per alcuni paesi durante l’acquisto](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
