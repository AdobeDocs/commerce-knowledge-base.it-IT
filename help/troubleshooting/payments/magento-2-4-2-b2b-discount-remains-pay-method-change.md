---
title: 'Adobe Commerce 2.4.2 B2B: lo sconto rimane la modifica del metodo di pagamento'
description: Questo articolo descrive un problema noto di Adobe Commerce 2.4.2 B2B in cui uno sconto legato al metodo di pagamento persiste dopo una modifica del metodo di pagamento al momento del pagamento. Al momento non è disponibile alcuna risoluzione.
exl-id: cd863852-403b-404f-8717-c78c238f5f33
feature: B2B, Orders, Payments, Personalization
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---

# Adobe Commerce 2.4.2 B2B: lo sconto rimane la modifica del metodo di pagamento

Questo articolo descrive un problema noto di Adobe Commerce 2.4.2 B2B in cui uno sconto legato al metodo di pagamento persiste dopo una modifica del metodo di pagamento al momento del pagamento. Al momento non è disponibile alcuna risoluzione.

## Prodotti e versioni interessati

* Adobe Commerce 2.4.2
* Adobe Commerce sull’infrastruttura cloud 2.4.2
* B2B per Adobe Commerce 1.3.1


## Problema

<u>Passaggi da riprodurre</u>:

1. Crea un carrello **Regola prezzo** legato a un metodo di pagamento (esempio: gli utenti Paypal ricevono uno sconto del 20%).
1. Creare un ordine di acquisto e selezionare Paypal come metodo di pagamento. Viene applicato lo sconto.
1. L&#39;ordine di acquisto viene approvato.
1. Vai alla pagina di pagamento per completare l&#39;ordine.
1. Seleziona un altro metodo di pagamento.

<u>Risultati effettivi</u>:

Lo sconto per il metodo di pagamento rimane applicato al totale dell&#39;ordine.  Non viene visualizzato alcun messaggio di errore. Il proprietario dell&#39;archivio sarà in grado di visualizzare questo problema verificatosi verificando la cronologia degli ordini.

<u>Risultati previsti</u>: lo sconto per il metodo di pagamento viene rimosso dal totale dell&#39;ordine, come previsto.

## Soluzione

Al momento non è disponibile alcuna risoluzione.
