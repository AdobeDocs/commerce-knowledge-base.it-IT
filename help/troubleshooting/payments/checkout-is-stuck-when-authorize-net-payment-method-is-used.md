---
title: Il pagamento è bloccato quando si utilizza il metodo di pagamento Authorize.net
description: Questo articolo fornisce una spiegazione e una correzione per il problema di Adobe Commerce 2.3.X in cui l’estrazione si blocca se viene utilizzato Authorize.net, con il messaggio di errore *’Impossibile leggere la proprietà "length" di null"* nel registro della console del browser.
exl-id: 01dc1147-4010-4dc5-81f3-3b3015a8c47c
feature: Cache, Checkout, Console, Orders, Payments
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: c4af0798-d497-5e6b-8380-19812c26d00a
    internal-label: Console
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%
---
# Il pagamento è bloccato quando si utilizza il metodo di pagamento Authorize.net

Questo articolo fornisce una spiegazione e una correzione per il problema di Adobe Commerce 2.3.X in cui l&#39;estrazione si blocca se si utilizza Authorize.net, con il messaggio di errore *&#39;Impossibile leggere la proprietà &#39;length&#39; di null&#39;* nel registro della console del browser.

## Prodotti e versioni interessati

* Adobe Commerce 2.3.X

>[!NOTE]
>
>L’integrazione del pagamento Adobe Commerce Authorize.Net di base è diventata obsoleta a partire dalla versione 2.3.4 ed è stata completamente rimossa nella versione 2.4.0. Utilizza invece un&#39;estensione adatta alle tue esigenze da [Adobe Commerce [!DNL Marketplace]](https://commercemarketplace.adobe.com/).

## Problema

<u>Passaggi da riprodurre</u>

1. Configura il metodo di pagamento Authorize.net in Commerce Admin.
1. Vai alla vetrina.
1. Aggiungi un prodotto al carrello e procedi al pagamento.
1. Scegli Authorize.net come metodo di pagamento.
1. Fai clic su **Inserisci ordine**.

<u>Risultato previsto</u>

L’iframe Authorize.net è caricato.

<u>Risultato effettivo</u>

Viene visualizzato Ajax spinner e la pagina non si carica mai. Nel registro della console del browser viene visualizzato il seguente errore JS: *&#39;TypeError non rilevato: impossibile leggere la proprietà &#39;length&#39; di null in b (jstest.authorize.net/v1/AcceptCore.js:1)&#39;*

## Causa

Uno dei motivi più comuni di questo problema è che la chiave del client pubblico non è specificata nella configurazione Authorize.Net in Commerce Admin.

## Soluzione

In **Archivi** > **Impostazioni** > **Configurazione** > **Vendite** > **Metodi di pagamento**, nella sezione **Autorizza.net**, verifica se il valore è specificato nel campo **Chiave client pubblica**. Se è vuoto, immetti il valore chiave dall&#39;account esercente Authorize.Net.

Per applicare le modifiche, pulire la cache eseguendo

```bash
bin/magento cache:clean
```
