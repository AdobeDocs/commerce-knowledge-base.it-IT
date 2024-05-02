---
title: Messaggio di errore durante l’aggiunta di siti a Security Scan
description: Questo articolo fornisce possibili soluzioni al problema che si verifica quando un utente non è in grado di aggiungere siti a [Commerce Security Scan](https://account.magento.com/scanner/dashboard/).
exl-id: 8d000ca4-b977-432d-bb26-6ea320067a40
feature: Cache, Compliance, Console, Security
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# Messaggio di errore durante l’aggiunta di siti a Security Scan

Questo articolo fornisce possibili soluzioni al problema che si verifica quando un utente non è in grado di aggiungere siti a [Commerce Security Scan](https://account.magento.com/scanner/dashboard/).

## Prodotti e versioni interessati

* Adobe Commerce (tutti i metodi e le versioni di distribuzione)
* Magento Open Source

## Problema

L’utente non è in grado di aggiungere siti a [Commerce Security Scan](https://account.magento.com/scanner/dashboard/). Quando si tenta di aggiungere un sito viene visualizzato il seguente messaggio di errore: *Impossibile inviare il sito per la scansione.*

## Soluzione

1. Verificare che i seguenti indirizzi IP non siano bloccati sulle porte 80 e 443:
   * 52 87 98 44
   * 34 196 167 176
   * 3 218 25 102

1. Il codice di conferma è sensibile al tempo. Se sono trascorsi più di 30 minuti dopo il **Aggiungi sito** clic sul collegamento, il codice è probabilmente scaduto.
1. Non dimenticare di pulire la cache e accertati che il codice di convalida venga visualizzato nel corpo del codice sorgente della pagina iniziale. Il codice di conferma deve essere inserito in base alle specifiche di markup HTML: il commento HTML può essere inserito nel corpo della pagina (si consiglia di inserirlo nella sezione piè di pagina); il tag META deve essere presente solo nella sezione head.
1. Prima di fare clic **Verifica codice di conferma**, apri la Developer Console del browser, fai clic su **Rete** e controlla la risposta da magento.com. Deve essere HTTP 200 (OK) e il corpo della risposta deve contenere un oggetto JSON.
1. Se il codice di risposta è HTTP 200 e il corpo della risposta è un oggetto JSON e il `verified` valore proprietà: `false`, significa che il codice non è stato trovato nella pagina. Il `details` Il valore della proprietà deve contenere la spiegazione. Ad esempio, se l’archivio utilizza un certificato SSL autofirmato, probabilmente si verificherà un errore di connessione.

Se non riesci ancora ad aggiungere siti, completa i passaggi seguenti:

1. Inserisci un altro commento di HTML sulla pagina:

   ```HTML
   <!-- MAGEID:Your magento.com ID, EMAIL:your email address -->
   ```

1. Invia un ticket di supporto e fornisci le seguenti informazioni:
   * URL store di Adobe Commerce
   * E-mail account MAGEID + Magento.com
   * Nome + Cognome
   * Nome dell’azienda
   * Elenco e-mail di notifica separato da virgole

## Lettura correlata

* [Security Scan](https://docs.magento.com/user-guide/magento/security-scan.html) nella guida utente.
