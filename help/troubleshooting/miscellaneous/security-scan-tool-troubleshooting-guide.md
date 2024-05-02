---
title: Guida alla risoluzione dei problemi relativi allo strumento Adobe Commerce Security Scan
description: Scopri come risolvere i vari problemi con lo strumento Security Scan per Adobe Commerce e Magento Open Source.
exl-id: 35e18a11-bda9-47eb-924a-1095f4f01017
feature: Compliance, Security
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '859'
ht-degree: 0%

---

# Guida alla risoluzione dei problemi relativi allo strumento Adobe Commerce Security Scan

Scopri come risolvere i vari problemi con lo strumento Security Scan per Adobe Commerce e Magento Open Source.

## Problema: impossibile inviare il sito

Lo strumento Security Scan richiede di dimostrare la proprietà del sito prima che il dominio possa essere aggiunto allo strumento Security Scan. Questa operazione può essere eseguita aggiungendo un codice di conferma al sito utilizzando un commento di HTML o `<meta>` tag. Il commento HTML deve essere inserito all’interno del `<body>` , ad esempio nella sezione piè di pagina. Il `<meta>` il tag deve essere inserito all’interno del `<head>` sezione.

Un problema comune riscontrato dai commercianti si verifica quando lo strumento Security Scan non è in grado di confermare la proprietà del sito del commerciante.

Se ricevi un errore e non riesci a inviare il sito per la scansione, fai riferimento a [Messaggio di errore durante l’aggiunta di siti a Security Scan](/help/troubleshooting/miscellaneous/error-message-adding-site-into-security-scan.md) articolo sulla risoluzione dei problemi nella knowledge base di supporto.

## Problema: rapporti vuoti generati dallo strumento Security Scan

Ottieni rapporti di scansione vuoti dallo strumento Security Scan (Scansione di sicurezza) o rapporti contenenti un solo errore come *Lo strumento di sicurezza non è riuscito a raggiungere l’URL di base* o *Impossibile trovare l&#39;installazione di Magento nell&#39;URL specificato*.

### Soluzione

1. Verificare che gli IP 52.87.98.44, 34.196.167.176 e 3.218.25.102 non siano bloccati alle porte 80 e 443.
1. Controlla l’URL inviato per verificare la presenza di reindirizzamenti (ad esempio, `https://mystore.com` reindirizza a `https://www.mystore.com` o viceversa o viene reindirizzato ad altri nomi di dominio).
1. Esaminare i registri di accesso WAF/server Web per le richieste rifiutate/non soddisfatte. HTTP 403 `Forbidden` e HTTP 500 `Internal server error` sono le risposte comuni del server che generano rapporti vuoti. Di seguito è riportato un esempio di codice di conferma che blocca le richieste da parte degli agenti utente:

```code block
if(req.http.user-agent ~ "(Chrome|Firefox)/[1-7][0-9]" && client.ip !~ useragent_allowlist)

{   error 403;   }
```

Puoi anche vedere [Il report dello strumento Security Scan è vuoto](/help/troubleshooting/miscellaneous/the-security-scan-tool-report-is-blank.md) articolo nella knowledge base di supporto per ulteriori informazioni.

## Problema: il problema di sicurezza è stato risolto ma è ancora visualizzato come vulnerabile durante l’analisi

È stato risolto un problema di sicurezza e si prevede che l&#39;analisi della sicurezza mostri che l&#39;utente non è più vulnerabile al problema appena risolto. Al contrario, il rapporto generato dall’analisi della sicurezza segnala ancora l’utente come vulnerabile al problema di sicurezza.

### Causa

I metadati dell’istanza cloud vengono raccolti solo per `active` e `live` Progetti cloud e NON è un processo in tempo reale.

Lo script di raccolta delle statistiche viene eseguito una volta al giorno, quindi lo strumento Security Scan deve raccogliere i nuovi dati in un secondo momento.

La latenza prevista per il ciclo di sincronizzazione è di una settimana e richiede almeno 24 ore.

Gli stati seguenti possono essere visualizzati dai controlli:

1. **Superato**: lo strumento Security Scan ha analizzato i dati aggiornati e approvato le modifiche.
1. **Sconosciuto**: lo strumento Security Scan non contiene ancora dati sul dominio. Attendere il successivo ciclo di sincronizzazione.
1. **Non riuscito**: se lo stato non viene visualizzato, è necessario risolvere il problema (abilita 2FA, cambia l’URL dell’amministratore, ecc.) e attendere il successivo ciclo di sincronizzazione.

Se sono trascorse 24 ore dalle modifiche apportate all’istanza e non vengono riportate nel rapporto Security Scan, puoi [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket). Immetti l’URL dello store durante l’invio del ticket.

## Errore sospetto BotNet

Ricevi una notifica relativa al guasto &quot;BotNet Suspect&quot;.

### Causa

1. Il nome del dominio dello store è entrato in un &quot;Potential BotNet Participants List&quot; nel 2019, e aveva il pannello di amministrazione, il downloader, o la funzionalità RSS pubblicamente esposto, e/o il suo URL è stato menzionato nei forum CC skimming.
1. L’avviso potrebbe essere causato dai segni di compromissione dello store e/o da malware, come JavaScript trovato nella pagina.
1. Non si tratta necessariamente di una questione in corso. Se il negozio è stato compromesso in precedenza, il suo nome host può ancora fluttuare intorno al web oscuro come un nome &quot;vittima&quot;.
1. Potrebbe anche essere causato non da Adobe Commerce, ma da un compromesso di sistema (a livello di sistema operativo).

### Soluzione

1. Controlla se sono stati creati nuovi account SSH, modifiche al file system e così via.
1. Eseguire un&#39;analisi della protezione.
1. Controlla la versione e l’aggiornamento di Adobe Commerce, soprattutto se è ancora in esecuzione il Magento 1, che non è più supportato.
1. Se il problema persiste, [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) e fornisci l’URL dello store.

## Problema: errore di inserimento compromissione

Riceve un errore relativo a un errore di &quot;Iniezione compromessa&quot;.

### Soluzione

1. Esaminare gli script indicati nel report relativo allo strumento Security Scan.
1. Controlla il corpo sorgente della pagina iniziale per le iniezioni di script in linea.
1. Eseguire la revisione delle modifiche alla configurazione del sistema, in particolare quelle personalizzate `HTML head` e `Miscellaneous HTML` in `footer` valori di sezione.
1. Eseguire la revisione del codice e del database per individuare eventuali modifiche e segni di malware iniettato.

Se nessuna delle condizioni sopra descritte può essere d’aiuto, [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) e fornisci l’URL dell’archivio e il messaggio di errore dal rapporto.

## Domande frequenti

### L&#39;analisi della sicurezza influisce sulle prestazioni del sito Web?

No. Security Scan effettua tutte le richieste una alla volta come un singolo utente. Per questo motivo, l&#39;analisi della sicurezza non dovrebbe influire sulle prestazioni del sito Web.

### Per quanto tempo Adobe Commerce conserva i rapporti Security Scan?

Puoi generare i 10 rapporti precedenti dalla tua fine. Se sono necessari rapporti precedenti, contatta il supporto Adobe Commerce. È possibile ottenere fino a un anno di rapporti Security Scan precedenti.

### Quali informazioni sono necessarie per inviare un ticket di supporto?

Assicurarsi di specificare il nome di dominio.
