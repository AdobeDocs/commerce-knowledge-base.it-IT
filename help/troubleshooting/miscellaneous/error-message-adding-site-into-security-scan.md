---
title: Messaggio di errore durante l’aggiunta di siti a Security Scan
description: Questo articolo fornisce possibili soluzioni al problema che si verifica quando un utente non è in grado di aggiungere siti a [Commerce Security Scan](https://account.magento.com/scanner/dashboard/).
exl-id: 8d000ca4-b977-432d-bb26-6ea320067a40
feature: Cache, Compliance, Console, Security
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
    internal-label: Compliance
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
    internal-label: Security
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
source-wordcount: '367'
ht-degree: 0%
---
# Messaggio di errore durante l’aggiunta di siti a Security Scan

In questo articolo vengono fornite possibili soluzioni per il problema che si verifica quando un utente non è in grado di aggiungere siti all&#39;[analisi della sicurezza di Commerce](https://account.magento.com/scanner/dashboard/).

## Prodotti e versioni interessati

* Adobe Commerce (tutti i metodi e le versioni di distribuzione)
* Magento Open Source

## Problema

L&#39;utente non è in grado di aggiungere siti all&#39;[Analisi sicurezza di Commerce](https://account.magento.com/scanner/dashboard/). Durante il tentativo di aggiungere un sito viene visualizzato il seguente messaggio di errore: *Impossibile inviare il sito per la scansione.*

## Soluzione

1. Verificare che i seguenti indirizzi IP non siano bloccati sulle porte 80 e 443:
   * 52.87.98.44
   * 34.196.167.176
   * 3.218.25.102

1. Il codice di conferma è sensibile al tempo. Se sono trascorsi più di 30 minuti dopo che è stato fatto clic sul collegamento **Aggiungi sito**, è probabile che il codice sia scaduto.
1. Non dimenticare di pulire la cache e accertati che il codice di convalida venga visualizzato nel corpo del codice sorgente della pagina iniziale. Il codice di conferma deve essere inserito in base alle specifiche di markup di HTML: il commento HTML può essere inserito nel corpo della pagina (si consiglia di inserirlo nella sezione piè di pagina); il tag META deve essere presente solo nella sezione head.
1. Prima di fare clic su **Verifica codice di conferma**, apri la console per sviluppatori del browser, fai clic sulla scheda **Rete** e controlla la risposta da magento.com. Deve essere HTTP 200 (OK) e il corpo della risposta deve contenere un oggetto JSON.
1. Se il codice di risposta è HTTP 200 e il corpo della risposta è un oggetto JSON e il valore della proprietà `verified` è `false`, significa che il codice non è stato trovato nella pagina. Il valore della proprietà `details` deve contenere la spiegazione. Ad esempio, se l’archivio utilizza un certificato SSL autofirmato, probabilmente si verificherà un errore di connessione.

Se non riesci ancora ad aggiungere siti, completa i passaggi seguenti:

1. Inserisci un altro commento HTML sulla pagina:

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

* [Analisi protezione](https://experienceleague.adobe.com/it/docs/commerce-admin/systems/security/security-scan) nella guida utente.
