---
title: Blocca il traffico dannoso per Adobe Commerce a livello Fastly
description: Questo articolo descrive i passaggi da seguire per bloccare traffico dannoso se si sospetta che l’archivio Adobe Commerce su infrastruttura cloud stia avendo un attacco DDoS.
exl-id: 1a834a0a-753b-432e-9c3b-ef8dd034d294
feature: Cache, Marketing Tools
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 0%

---

# Blocca il traffico dannoso per Adobe Commerce a livello Fastly

Questo articolo descrive i passaggi da seguire per bloccare traffico dannoso se si sospetta che l’archivio Adobe Commerce su infrastruttura cloud stia avendo un attacco DDoS.

## Prodotti e versioni interessati:

* Adobe Commerce sull’infrastruttura cloud 2.3.x

In questo articolo supponiamo che tu disponga già di IP dannosi e/o del loro paese e dei loro agenti utente. In genere, gli utenti di Adobe Commerce su infrastrutture cloud ricevono queste informazioni dal supporto Adobe Commerce. Le sezioni seguenti forniscono i passaggi per bloccare il traffico in base a queste informazioni. Tutte le modifiche devono essere effettuate nell’ambiente di produzione.

## Accedere al pannello di amministrazione

Se il tuo sito web è sovraccaricato da DDoS, potresti non essere in grado di accedere al tuo amministratore Commerce (ed eseguire tutti i passaggi descritti più avanti in questo articolo).

Per accedere all’amministratore, imposta il sito web in modalità di manutenzione come descritto in [Attiva o disattiva la modalità di manutenzione](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html#instgde-cli-maint) e inserire in una whitelist il tuo indirizzo IP. Al termine, disattiva la modalità di manutenzione.

## Blocca traffico per IP

Per l’archivio infrastrutture cloud di Adobe Commerce, il modo più efficace per bloccare il traffico in base a indirizzi IP e subnet specifici è quello di aggiungere un ACL per Fastly nell’amministratore Commerce. Di seguito sono riportati i passaggi con collegamenti a istruzioni più dettagliate:

1. In Amministrazione Commerce, passa a **Negozi** > **Configurazione** > **Avanzate** > **Sistema** > **Cache a pagina intera** > **Configurazione rapida**.
1. [Crea un nuovo ACL](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/ACL.md) con un elenco di indirizzi IP o subnet che stai per bloccare.
1. Aggiungilo all&#39;elenco ACL e blocca come descritto nella sezione [Blocco](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/BLOCKING.md) guida per il modulo Fastly\_Cdn per Adobe Commerce.

## Blocca traffico per paese

Per l’archivio infrastrutture cloud di Adobe Commerce, il modo più efficace per bloccare il traffico per paese/i è aggiungere un ACL per Fastly nell’amministratore Commerce.

1. In Amministrazione Commerce, passa a **Negozi** > **Configurazione** > **Avanzate** > **Sistema** > **Cache a pagina intera** > **Configurazione rapida**.
1. Seleziona i paesi e configura il blocco utilizzando ACL come descritto in [Blocco](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/BLOCKING.md) guida per il modulo Fastly\_Cdn per Adobe Commerce.

## Blocca traffico per agente utente

Per stabilire il blocco in base all’agente utente, devi aggiungere uno snippet VCL personalizzato alla configurazione Fastly. A questo scopo, effettua le seguenti operazioni:

1. In Amministrazione Commerce, passa a **Negozi** > **Configurazione** > **Avanzate** > **Sistema** > **Cache a pagina intera**.
1. Then **Configurazione rapida** > **Snippet VCL personalizzati**.
1. Creare il nuovo snippet personalizzato come descritto nella [Snippet VCL personalizzati](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/CUSTOM-VCL-SNIPPETS.md) per il modulo Fastly\_Cdn. Puoi utilizzare il seguente codice di esempio. Questo esempio non consente il traffico per `AhrefsBot` e `SemrushBot` agenti utente.

```php
name: block_bad_useragents
  type: recv
  priority: 5
  VCL:
  if ( req.http.User-Agent ~ "(AhrefsBot|SemrushBot)" ) {
      error 405 "Not allowed";
  }
```

## Limitazione della velocità (funzionalità sperimentale Fastly)

È disponibile una funzionalità sperimentale Fastly per Adobe Commerce sull’infrastruttura cloud che consente di specificare il limite di velocità per determinati percorsi e crawler. Fai riferimento a [Documentazione del modulo Fastly](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/RATE-LIMITING.md) per i dettagli.

La funzionalità deve essere sottoposta a test approfonditi nell’ambiente di staging, prima di essere utilizzata in produzione, perché potrebbe bloccare il traffico legittimo.

## Consigliato: è consigliabile aggiornare robots.txt

Aggiornamento di `robots.txt` il file può essere utile per evitare che determinati motori di ricerca, crawler e robot eseguano la ricerca per indicizzazione di determinate pagine. Esempi di pagine che non devono essere sottoposte a ricerca per indicizzazione sono le pagine dei risultati di ricerca, il pagamento, le informazioni sui clienti e così via. Impedire ai robot di eseguire la ricerca per indicizzazione di queste pagine potrebbe aiutare a ridurre il numero di richieste generate da quei robot.

Quando si utilizza, è necessario tenere presenti due considerazioni `robots.txt`:

* I robot possono ignorare `robots.txt`. Soprattutto i robot malware, che scansionano il web per individuare vulnerabilità di sicurezza, e i raccoglitori di indirizzi e-mail utilizzati da spammer non presteranno attenzione.
* Il `robots.txt` file disponibile pubblicamente. Chiunque può vedere quali sezioni del server non si desidera che i robot utilizzino.

Informazioni di base e Adobe Commerce predefinito `robots.txt` La configurazione di può essere trovata in [Robot motore di ricerca](https://docs.magento.com/m2/ee/user_guide/marketing/search-engine-robots.html) articolo nella documentazione per gli sviluppatori.

Per informazioni generali e raccomandazioni su `robots.txt`, vedi:

* [Creare un file robots.txt](https://developers.google.com/search/docs/advanced/robots/create-robots-txt) file per supporto Google
* [Informazioni su /robots.txt](https://www.robotstxt.org/robotstxt.html) da robotstxt.org

Collabora con il tuo sviluppatore e/o esperto di SEO per determinare quali agenti utente vuoi consentire o quelli che desideri disabilitare.

## Lettura correlata

[Condizioni di licenza specifiche per Adobe Commerce su Cloud](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/PSLT-AdobeCommerceCloud-WW-2023v1.pdf)
