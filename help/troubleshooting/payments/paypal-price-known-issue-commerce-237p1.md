---
title: "Adobe Commerce 2.3.7-p1 problema noto: totale ordini obsoleti per PayPal"
description: "Questo articolo fornisce una patch per un problema noto in Adobe Commerce 2.3.7-p1: quando si utilizza PayPal Checkout più di una volta i clienti ottengono il prodotto ordinato in precedenza nel carrello, invece di quello nuovo che stanno cercando di ordinare."
exl-id: ceb8f7ad-0cf7-4d42-aded-25d1dd947f5b
feature: Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# Adobe Commerce 2.3.7-p1 problema noto: totale ordini obsoleti per PayPal

Questo articolo fornisce una patch per un problema noto in Adobe Commerce 2.3.7-p1: quando si utilizza PayPal Checkout più di una volta i clienti ottengono il prodotto ordinato in precedenza nel carrello, invece di quello nuovo che stanno cercando di ordinare.
La patch può essere scaricata da questo articolo ed è disponibile anche tramite lo strumento Quality Patches (QPT).

## Versioni interessate

* Adobe Commerce (tutte le opzioni di implementazione) 2.3.7-p1
* Magento Open Source 2.3.7-p1

## Problema

Quando si effettua un ordine utilizzando il metodo di pagamento PayPal Express Checkout, il prodotto acquistato precedentemente ordinato viene aggiunto all&#39;ordine al posto di quello effettivo.

<u>Passaggi da riprodurre:</u>

1. Sulla vetrina, aggiungi qualsiasi prodotto al carrello (prodotto A, prezzo 50 $).
1. Fai clic sul collegamento del carrello per aprire il carrello.
1. Fai clic su **Pagamento PayPal** pulsante.
1. Utilizza le credenziali PayPal per accedere a PayPal e inviare il pagamento.
1. Terminare il posizionamento dell&#39;ordine sul lato del negozio.
1. Torna al catalogo e aggiungi un prodotto diverso (prodotto B, prezzo $ 100) al carrello.
1. Fai clic sul collegamento del carrello per aprire il carrello.
1. Fai clic su **Pagamento PayPal** pulsante.

<u>Risultato effettivo:</u>

Il prezzo del prodotto nel carrello è di $50 invece di $100.<br/>
Sul lato negozio, l&#39;ordine contiene il prodotto A invece del prodotto B.

<u>Risultato previsto:</u>

Il prodotto B viene aggiunto all’ordine.

## Soluzione

Applichi la patch fornita in questo articolo.

## Patch

Utilizza il seguente collegamento per scaricare un file .zip contenente la patch: [MC42674-compositore.patch.zip](assets/MC42674-composer.patch.zip).

### Versioni compatibili di Adobe Commerce

* Adobe Commerce (tutte le opzioni di implementazione) 2.3.7-p1

## Come applicare i cerotti

1. Decomprimi il file .zip scaricato.
1. Consulta [Come applicare una patch del compositore fornita dall&#39;Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) per ulteriori istruzioni.
