---
title: Il pagamento è bloccato quando si utilizza il metodo di pagamento Authorize.net
description: Questo articolo fornisce una spiegazione e una correzione per il problema di Adobe Commerce 2.3.X in cui l’estrazione si blocca se viene utilizzato Authorize.net, con il messaggio di errore *’Impossibile leggere la proprietà "length" di null"* nel registro della console del browser.
exl-id: 01dc1147-4010-4dc5-81f3-3b3015a8c47c
feature: Cache, Checkout, Console, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Il pagamento è bloccato quando si utilizza il metodo di pagamento Authorize.net

Questo articolo fornisce una spiegazione e una correzione per il problema di Adobe Commerce 2.3.X in cui il pagamento si blocca se si utilizza Authorize.net, con *&quot;Impossibile leggere la proprietà &quot;length&quot; di null&quot;* messaggio di errore nel registro della console del browser.

## Prodotti e versioni interessati

* Adobe Commerce 2.3.X

>[!NOTE]
>
>L’integrazione del pagamento Adobe Commerce Authorize.Net di base è diventata obsoleta a partire dalla versione 2.3.4 ed è stata completamente rimossa nella versione 2.4.0. Utilizza un’estensione che soddisfi le tue esigenze dall’ [Adobe Commerce [!DNL Marketplace]](https://commercemarketplace.adobe.com/) invece.

## Problema

<u>Passaggi da riprodurre</u>

1. Configura il metodo di pagamento Authorize.net in Commerce Admin.
1. Vai alla vetrina.
1. Aggiungi un prodotto al carrello e procedi al pagamento.
1. Scegli Authorize.net come metodo di pagamento.
1. Clic **Inserisci ordine**.

<u>Risultato previsto</u>

L’iframe Authorize.net è caricato.

<u>Risultato effettivo</u>

Viene visualizzato Ajax spinner e la pagina non si carica mai. Nel registro della console del browser viene visualizzato il seguente errore JS: *&quot;TypeError non rilevato: impossibile leggere la proprietà &quot;length&quot; di null in b (jstest.authorize.net/v1/AcceptCore.js:1)&#39;)*

## Causa

Uno dei motivi più comuni di questo problema è che la chiave del client pubblico non è specificata nella configurazione Authorize.Net in Commerce Admin.

## Soluzione

Sotto **Negozi** > **Impostazioni** > **Configurazione** > **Vendite** > **Metodi di pagamento**, nella **Authorize.net** , verifica se il valore è specificato nella sezione **Chiave client pubblica** campo. Se è vuoto, immetti il valore chiave dall&#39;account esercente Authorize.Net.

Per applicare le modifiche, pulire la cache eseguendo

```bash
bin/magento cache:clean
```
