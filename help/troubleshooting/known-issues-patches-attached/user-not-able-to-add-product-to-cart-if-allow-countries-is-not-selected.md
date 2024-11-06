---
title: Gli utenti non possono aggiungere un prodotto al carrello se non è selezionato nulla in Paesi consentiti
description: Questo articolo fornisce una patch per il problema noto di Adobe Commerce 2.4.4 con PHP 8.1 in cui gli utenti non sono in grado di aggiungere prodotti al carrello se l’opzione Consenti paesi non è selezionata.
exl-id: d05d1956-de23-496c-9234-c461a3cfdf36
feature: Orders, Products, Shopping Cart
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---

# Gli utenti non possono aggiungere un prodotto al carrello se non è selezionato nulla in Paesi consentiti

Questo articolo fornisce una patch per il problema noto di Adobe Commerce 2.4.4 con PHP 8.1 in cui gli utenti non sono in grado di aggiungere prodotti al carrello se l’opzione Consenti paesi non è selezionata.

## Prodotti e versioni interessati

Adobe Commerce 2.4.4 con PHP 8.1

## Problema

Gli utenti non possono aggiungere prodotti al carrello se l’opzione Consenti paesi non è selezionata.

<u>Passaggi da riprodurre</u>:

1. Accedi all’amministratore di Commerce.
1. Vai a **Store** > **Configurazione** > **Generale** > **Opzioni paese**
1. Deseleziona tutte le opzioni nel campo **Consenti paesi**.
1. Fai clic su **Salva configurazione** per salvare la configurazione.
1. Vai alla vetrina e prova ad aggiungere un prodotto al carrello.

<u>Risultato previsto:</u>

Puoi aggiungere un prodotto al carrello.

<u>Risultato effettivo:</u>

Non puoi aggiungere un prodotto al carrello. Viene visualizzato il seguente errore della console:

```bash
Failed to load resource: the server responded with a status of 400 (Bad Request)
customer-data.js:87 Uncaught Error: [object Object]
    at Object.<anonymous> (customer-data.js:87:23)
    at fire (jquery.js:3500:50)
    at Object.fireWith [as rejectWith] (jquery.js:3630:29)
    at done (jquery.js:9798:30)
    at XMLHttpRequest.<anonymous> (jquery.js:10057:37)
```

## Causa

La configurazione di Adobe Commerce recupera `null` nel caso in cui una configurazione a selezione multipla non contenga elementi selezionati. Questa configurazione se ulteriormente elaborata correttamente nelle versioni PHP precedenti alla 8.1. Tuttavia in PHP 8.1 non funziona correttamente a causa degli errori causati da &quot;[Deprecate passando null ad argomenti non nullable di funzioni interne in PHP 8.1](https://wiki.php.net/rfc/deprecate_null_to_scalar_internal_arg)&quot;.

## Soluzioni

Per risolvere il problema, applica la seguente patch:

[AC-2655_2.4.4.patch.zip](assets/AC-2655_2.4.4.patch.zip)

## Come applicare il cerotto

Per istruzioni, consulta [Come applicare una patch del compositore fornita da Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) nella Knowledge Base di supporto.

## Collegamenti utili

[Applica patch personalizzate ad Adobe Commerce sull&#39;infrastruttura cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.
