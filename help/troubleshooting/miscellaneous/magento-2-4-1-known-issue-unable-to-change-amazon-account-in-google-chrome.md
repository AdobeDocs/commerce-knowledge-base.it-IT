---
title: "Problema Adobe Commerce 2.4.1: impossibile modificare l’account Amazon in Chrome"
description: Questo articolo descrive un problema noto di Adobe Commerce 2.4.1 in cui i clienti accedono agli account Amazon utilizzati in precedenza invece di essere suggeriti per l’accesso, quando utilizzano Amazon Pay durante il pagamento.
exl-id: 8acffe99-b3ec-4b45-9434-61b66e963838
feature: Customer Service
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# Problema Adobe Commerce 2.4.1: impossibile modificare l’account Amazon in Chrome

Questo articolo descrive un problema noto di Adobe Commerce 2.4.1 in cui i clienti accedono agli account Amazon utilizzati in precedenza invece di essere suggeriti per l’accesso, quando utilizzano Amazon Pay durante il pagamento.

## Prodotti e versioni interessati

* Adobe Commerce on-premise 2.4.1
* Adobe Commerce sull’infrastruttura cloud 2.4.1

## Problema

Quando si utilizza Amazon Pay durante il pagamento, i clienti accedono agli account Amazon utilizzati in precedenza anziché ricevere suggerimenti per l’accesso.

<u>Passaggi da riprodurre:</u>

1. Nella vetrina, aggiungi qualsiasi elemento al carrello e procedi al pagamento come ospite.
1. Fai clic sul pulsante **Amazon Pay**. Viene visualizzato il pop-up di accesso a Amazon.com.
1. Accedi all’account Amazon.
1. Seleziona un indirizzo e fai clic su **Avanti**.
1. Seleziona il metodo di pagamento.
1. Fai clic su **Ordina**.
1. Torna alla home page e accedi all’account del negozio.
1. Aggiungi di nuovo qualsiasi elemento al carrello e procedi al pagamento.
1. Fai clic sul pulsante **Amazon Pay**.

<u>Risultato effettivo:</u>

Effettua di nuovo l’accesso automatico all’account Amazon utilizzato in precedenza (Passaggio 3).

<u>Risultato previsto:</u>

Viene visualizzata una finestra a comparsa per l&#39;accesso a Amazon.com e puoi effettuare l&#39;accesso o creare un nuovo account per Amazon Pay.

## Causa

Il problema può verificarsi in una delle seguenti situazioni:

* Quando il valore del cookie `SameSite` è `LAX`, il cookie non verrà inviato come parte di chiamate di terze parti.
* La funzione di blocco dei contenuti di Mozilla Firefox impedisce a terzi di monitorare le attività degli utenti del browser bloccando l’utilizzo di script e meccanismi di archiviazione lato client. Firefox utilizza un fornitore esterno, Disconnect.me, per fornire un elenco di siti di tracciamento da bloccare. Amazon Pay utilizza un iframe in un sito web di terze parti per restituire un token di accesso dopo l’accesso ed eseguire il rendering del widget Indirizzo e wallet. Con la funzione di blocco dei contenuti, le richieste di caricamento degli iframe in Amazon Pay vengono considerate come richieste di tracciamento di terze parti e vengono bloccate, impedendo all’acquirente di procedere con il pagamento.
* Qualsiasi situazione in cui i cookie di terze parti o JS vengono bloccati esplicitamente dal browser.

## Soluzione

Assicurati che le richieste iframe di Amazon Pay non siano bloccate dai browser.
