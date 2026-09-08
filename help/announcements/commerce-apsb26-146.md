---
title: Azione urgente Richiesta Aggiornamento della sicurezza critica disponibile per Adobe Commerce (APSB26-146)
description: Adobe ha rilasciato il bollettino sulla sicurezza APSB26-146 relativo a CVE-2026-75650, una vulnerabilità di giorno zero in Adobe Commerce. Scopri come applicare l’hotfix e ruotare le credenziali.
autotag-review: '2026-09-07T17:27:44.037Z'
TQID: 'https://experienceleague.adobe.com/ADVRRn85--ZgWtPdi4qA49fsDPVW976N4MYWp26taho'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
  - id: c32adafa-ed01-4b31-997e-2413013911b0
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: e4cb6392735e3adb609d8cbd78548edff7f99570
workflow-type: tm+mt
source-wordcount: 852
ht-degree: 0%

---


# Azione urgente richiesta: aggiornamento critico della sicurezza disponibile per Adobe Commerce (APSB26-146)

>[!IMPORTANT]
>
>Questo è un aggiornamento urgente relativo a CVE-2026-75650. Adobe è consapevole del fatto che CVE-2026-75650 è stato sfruttato nel selvaggio targeting dei commercianti Adobe Commerce.

Il 7 settembre, Adobe ha rilasciato un aggiornamento critico sulla sicurezza che interessava Adobe Commerce e Magento Open Source. Adobe è venuto a conoscenza di una vulnerabilità a zero giorni in Adobe Commerce e ha rilasciato un aggiornamento sulla sicurezza (APSB26-146) per risolverla. La vulnerabilità potrebbe consentire a un utente non autenticato di eseguire codice arbitrario in un’installazione interessata (CVE-2026-75650).

Adobe ha rilasciato il bollettino sulla sicurezza APSB26-146, che affronta questa vulnerabilità. Il bollettino è disponibile al seguente indirizzo:

[Aggiornamento di sicurezza disponibile per Adobe Commerce | APSB26-146](https://helpx.adobe.com/security/products/magento/apsb26-146.html)

Questo articolo spiega come applicare l’hotfix per le versioni attuali e precedenti di Adobe Commerce e Magento Open Source.

## Descrizione

Prodotti e versioni interessati:

Versioni di Adobe Commerce:

* 2.4.9-2026-ago e versioni precedenti
* 2.4.8-2026-ago e versioni precedenti
* 2.4.7-2026-ago e versioni precedenti
* 2.4.6-2026-ago e versioni precedenti
* 2.4.5-2026-ago e versioni precedenti
* 2.4.4-2026-ago e versioni precedenti

Versioni B2B di Adobe Commerce:

* 1.5.3-2026-ago e versioni precedenti
* 1.5.2-2026-ago e versioni precedenti
* 1.4.2-2026-ago e versioni precedenti
* 1.3.4-2026-ago e versioni precedenti
* 1.3.3-2026-ago e versioni precedenti

Versioni di Magento Open Source:

* 2.4.9-2026-ago e versioni precedenti
* 2.4.8-2026-ago e versioni precedenti
* 2.4.7-2026-ago e versioni precedenti
* 2.4.6-2026-ago e versioni precedenti

## Risoluzione

### Soluzione per Adobe Commerce su cloud, Adobe Commerce on-premise e Magento Open Source

Per risolvere la vulnerabilità dei prodotti e delle versioni interessati, è necessario applicare la patch VULN-39341 (a seconda della versione) e ruotare le chiavi di crittografia.

Nota sulla compatibilità: tieni presente che questo hotfix è stato testato solo per le versioni elencate di seguito. Può funzionare su altre versioni supportate, ma questo non è stato ufficialmente verificato.

Versioni di Adobe Commerce:

* 2,4.9-2026-ago
* 2,4.8-2026-ago
* 2,4.7-2026-ago
* 2,4.6-2026-ago
* 2,4.5-2026-ago
* 2,4.4-2026-ago

Versioni B2B di Adobe Commerce:

* 1,5.3-2026-ago
* 1,5.2-2026-ago
* 1,4.2-2026-ago
* 1,3.4-2026-ago
* 1,3.3-2026-ago

Versioni di Magento Open Source:

* 2,4.9-2026-ago
* 2,4.8-2026-ago
* 2,4.7-2026-ago
* 2,4.6-2026-ago

### Collegamento hotfix

Applica il seguente hotfix alla versione del prodotto interessata:

* [Scarica l’Hotfix VULN-39341-compositore-patches.zip](https://repo.magento.com/patch/VULN-39341-composer-patches.zip)

### Come applicare l’hotfix

Decomprimi il file e vedi [Come applicare una patch del compositore fornita da Adobe](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento) nella Knowledge Base di supporto per le istruzioni.

### Conferma l’applicazione dell’hotfix (solo per Adobe Commerce su Cloud Merchants)

Poiché non è possibile determinare facilmente se il problema è stato corretto, si consiglia di verificare se l’hotfix CVE-2026-75650 è stato applicato correttamente.

Per eseguire questa operazione, eseguire la procedura seguente, utilizzando il file `VULN-39341_Hotfix_COMPOSER.patch` come esempio:

1. [Installare lo strumento Patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/usage#install).
1. Eseguire il comando: `vendor/bin/magento-patches -n status | grep "39341\|Status"`.
1. Dovresti visualizzare un output simile a questo, dove questo esempio VULN-39341 restituisce lo stato Applicato:

| ID | Titolo | Categoria | Origine | Stato | Dettaglio |
|---|---|---|---|---|---|
| N/D | .../m2-hotfixes/VULN-39341_Hotfix_COMPOSER.patch | Altro | Locale | Applicato | Tipo di patch: Personalizzato |

### Ruota le credenziali dopo l’applicazione della patch

Per risolvere completamente il problema, ruotare non solo la chiave di crittografia, ma anche tutte le credenziali che potrebbero essere state crittografate o esposte utilizzando tale chiave, incluse le credenziali di server, API e integrazione.

>[!NOTE]
>
>La chiave di crittografia viene utilizzata per crittografare token di integrazione, credenziali del gateway di pagamento e token di automazione con privilegi di sistema. La sola rotazione della chiave di crittografia non invalida le credenziali che potrebbero essere già state esposte. Ruota tutte le credenziali associate alla loro origine (ad esempio, presso il gateway dei pagamenti o il servizio di terze parti), non solo in Commerce.

Per ruotare le credenziali, eseguire la procedura seguente:

1. Applica l’hotfix.
1. Abilita la modalità di manutenzione.
1. Disabilita esecuzione cron (comando Commerce su Cloud: `vendor/bin/ece-tools cron:disable`).
1. [Ruota le chiavi di crittografia](https://experienceleague.adobe.com/it/docs/commerce-admin/systems/security/encryption-key?lang=en).
1. Ruota tutte le password utente del pannello di amministrazione.
1. Disattivare e rigenerare tutti i token di integrazione REST/SOAP/GraphQL (**[!UICONTROL System]** > **[!UICONTROL Extensions]** > **[!UICONTROL Integrations]**).
1. Ruota i segreti del client OAuth per tutte le applicazioni di terze parti collegate.
1. Ruota le credenziali API del gateway pagamenti a livello di provider (Stripe, Braintree, Adyen, PayPal, ecc.).
1. Ruota le credenziali del database.
1. Ruota le chiavi SSH/deploy ed eventuali credenziali dell&#39;account cron o di servizio con privilegi di sistema.
1. Ruota le chiavi API per la spedizione, le imposte e altre estensioni integrate di terze parti.
1. Svuota la cache.
1. Abilita esecuzione cron (comando Commerce su Cloud: `vendor/bin/ece-tools cron:enable`).
1. Disattiva la modalità di manutenzione.
1. Solo Commerce su Cloud: ridistribuisci per applicare le nuove credenziali del database.

### Aggiornamenti di sicurezza

Aggiornamenti di sicurezza disponibili per Adobe Commerce:

* [Bollettino sulla sicurezza di Adobe (APSB26-146)](https://helpx.adobe.com/security/products/magento/apsb26-146.html)
* [Ultimi aggiornamenti di sicurezza disponibili per Adobe Commerce](https://helpx.adobe.com/security/products/magento.html)

### Lettura correlata

[Attivare o disattivare la modalità di manutenzione](https://experienceleague.adobe.com/it/docs/commerce-operations/installation-guide/tutorials/maintenance-mode?lang=en) nella Guida all&#39;installazione di Adobe Commerce
