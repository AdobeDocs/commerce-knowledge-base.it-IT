---
title: Errori 403 durante l’accesso a Site-Wide Analysis Tool (Strumento di analisi a livello di sito) su Adobe Commerce
description: Questo articolo fornisce una soluzione per gli errori 403 che si verificano quando si tenta di accedere allo strumento di analisi a livello di sito su Adobe Commerce.
exl-id: f24fad17-62d6-4a0f-bcba-983c3dbee3d7
feature: Observability
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# Errori 403 durante l’accesso a Site-Wide Analysis Tool (Strumento di analisi a livello di sito) su Adobe Commerce

Questo articolo fornisce una soluzione per gli errori 403 che si verificano quando si tenta di accedere allo strumento di analisi a livello di sito su Adobe Commerce.

## Prodotti e versioni interessati

Adobe Commerce su infrastruttura cloud 2.4.1 e versioni successive.

## Problema

Si verifica un errore 403 quando si tenta di accedere allo strumento di analisi a livello di sito.

<u>Passaggi da riprodurre:</u>

Accedi al pannello di amministrazione di Commerce e fai clic su **Rapporti** > *Approfondimenti sistema* > **Strumento di analisi a livello di sito**.

<u>Risultato previsto:</u>

È disponibile lo strumento di analisi a livello di sito.

<u>Risultato effettivo:</u>

Vedi: *Errore 403.*


## Soluzione

Per verificare che lo strumento di analisi a livello di sito disponga dell&#39;accesso corretto all&#39;applicazione, eseguire il comando seguente nella CLI. Sostituisci `<store URL>` con l’URL del tuo negozio:

```cURL
curl -sIL -X GET <store URL>/swat/key/index | grep HTTP
HTTP/2 403
```

Effettua delle operazioni in base al codice di risposta ottenuto.

### 403 Codice di risposta non consentito

Se il codice di risposta è 403, è possibile che la protezione da bot Cloudflare blocchi Site-Wide Analysis Tool. Per accedere allo strumento, inserisci in una whitelist i suoi IP:

* 107.23.33.174
* 3 225 9 244
* 3 88 83 85

### Correzione del codice di risposta 200 e dell’output JSON

Se la risposta è il codice 200 e l’output JSON corretti, [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) per risolvere il problema con l’accesso a Site-Wide Analysis Tool (Strumento di analisi a livello di sito).


### Codice di risposta 500 (errore irreversibile)

Se il codice di risposta è 500 (errore irreversibile), installare la patch MDVA-38526. Utilizzare uno dei seguenti collegamenti per scaricare la patch, a seconda del tipo di patch desiderato:

* Adobe Commerce su patch infrastruttura cloud: [MDVA-38526_EE_2.4.1-p1_v3.patch.zip](assets/MDVA-38526_EE_2.4.1-p1_v3.patch.zip)
* patch del compositore dell’infrastruttura cloud di Adobe Commerce: [MDVA-38526_EE_2.4.1-p1_COMPOSER_v3.patch.zip](assets/MDVA-38526_EE_2.4.1-p1_COMPOSER_v3.patch.zip)

La patch è applicabile per Adobe Commerce su infrastruttura cloud versioni 2.4.1 e successive.

### Risposta non JSON

Se l’output di risposta non è JSON, ciò potrebbe essere dovuto all’implementazione di PWA/Headless. Se utilizzi l’implementazione headless, aggiorna la configurazione UPWARD per ignorare le richieste ad Adobe Commerce Origin. A questo scopo, nell’amministrazione di Adobe Commerce, in **Negozi** > **Configurazione** > **Generale** > **Web** > **Configurazione UPWARD PWA** > **Inserire nell&#39;elenco Consentiti Nome anteriore**, aggiungi *swat*.

![Configurazione_upward](assets/upward_pwa.png)

Se non riesci ancora ad accedere a Site-Wide Analysis Tool (Strumento di analisi a livello di sito), al prossimo accesso al pannello di amministrazione di Commerce vai a **Rapporti** > *Approfondimenti sistema* > **Strumento di analisi a livello di sito**, [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

## Lettura correlata

* [Guida allo strumento di analisi a livello di sito](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/intro.html)
