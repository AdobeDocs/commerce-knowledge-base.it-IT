---
title: 'Web Application Firewall (WAF) basato su Fastly: le domande frequenti'
description: I Web Application Firewall (WAF) impediscono al traffico dannoso di entrare in siti e reti filtrando il traffico in base a una serie di regole di sicurezza. Il traffico che attiva una qualsiasi delle regole viene bloccato prima che possa danneggiare i siti o la rete.
exl-id: d977ea68-7d8c-4863-b026-acdc25d8c430
feature: Cache
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '1655'
ht-degree: 0%

---

# Web Application Firewall (WAF) basato su Fastly: le domande frequenti

## Come funziona il WAF cloud gestito di Adobe Commerce (con tecnologia Fastly)?

I firewall per applicazioni Web impediscono a [traffico dannoso](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) di accedere a siti e reti filtrando il traffico in base a una serie di regole di sicurezza. Il traffico che attiva una qualsiasi delle regole viene bloccato prima che possa danneggiare i siti o la rete.

Il cloud WAF di Adobe Commerce fornisce una policy WAF con un set di regole progettato per proteggere le applicazioni web Adobe Commerce da un’ampia gamma di attacchi.

WAF esamina il traffico web e quello dell’amministratore per identificare eventuali attività sospette. Valuta il traffico GET e POST (chiamate API HTTP) e applica il set di regole per determinare quale traffico bloccare. WAF è in grado di bloccare un&#39;ampia varietà di attacchi, tra cui attacchi SQL injection, attacchi di scripting tra siti, attacchi di exfiltrazione dei dati e violazioni del protocollo HTTP.

In qualità di servizio basato su cloud, WAF non richiede hardware o software per l&#39;installazione o la manutenzione. Fastly, un partner tecnologico esistente, fornisce il software e le competenze necessarie. Il loro WAF ad alte prestazioni, sempre attivo, risiede in ogni nodo della cache all’interno della rete di distribuzione globale di Fastly.

## WAF è disponibile per tutti i clienti cloud?

Sì, il servizio cloud WAF è incluso nell’abbonamento Adobe Commerce all’infrastruttura cloud sia per l’architettura del piano Starter di Adobe Commerce sull’infrastruttura cloud che per i piani dell’architettura del piano Pro di Adobe Commerce sull’infrastruttura cloud senza costi aggiuntivi. Il servizio WAF è disponibile negli ambienti di produzione e staging.

## WAF è conforme ai requisiti PCI DSS 6.6?

Sì.

## Se il mio account Adobe Commerce on cloud infrastructure gestisce siti su più domini, il profilo WAF è sintonizzato per ciascun dominio o collettivamente per tutti i domini?

Il WAF viene sintonizzato collettivamente per tutti i domini con un singolo account cloud.

## Quali regole vengono utilizzate per WAF?

La regola impostata nel profilo WAF applicato all’ambiente di produzione dell’infrastruttura cloud di Adobe Commerce si basa sul set di regole OWASP Top 10 Threat Protection, che tratta gli utilizzi più comuni per i servizi web. Contiene anche regole specifiche per Adobe Commerce sviluppate da TrustWave SpiderLabs. Il team di ricerca sulla sicurezza di Fastly ha inoltre aggiunto regole che proteggono il sito e la rete da attacchi comunemente noti: indirizzi IP non validi, agenti utente non validi e nodi di comando e controllo botnet noti. Abilitiamo le regole a livello di paranoia di OWASP 3 o inferiore, che fornisce una copertura di alta sicurezza.

## Come posso accedere ai registri?

Per inviare i registri al tuo strumento di registrazione, collabora con il tuo Technical Account Manager (TAM) per aggiungere un endpoint di registrazione in Fastly.

## Come si presenta una richiesta di blocco?

Una richiesta bloccata restituisce una pagina 403 con un identificatore di richiesta.

Puoi personalizzare questa pagina purché la personalizzazione includa l’identificatore della richiesta. Contatta il tuo account manager tecnico per maggiori dettagli.

## Come si aggiornano i set di regole di WAF? Quanto rapidamente una regola WAF può essere modificata o aggiornata e applicata a livello globale in produzione?

Come parte del servizio cloud WAF, Fastly gestisce gli aggiornamenti delle regole da terze parti commerciali, Fastly Research e open source. Aggiornano le regole pubblicate in un criterio in base alle esigenze o quando sono disponibili modifiche alle regole dalle rispettive origini. Le nuove regole che corrispondono alle classi pubblicate di regole vengono inserite anche nell’istanza WAF di qualsiasi servizio una volta attivato. Questo contribuisce a garantire una copertura immediata per gli exploit nuovi o in evoluzione. Puoi consultare le informazioni [sugli aggiornamenti e la manutenzione delle regole](https://docs.fastly.com/guides/web-application-firewall/fastly-waf-rule-set-updates-maintenance#rule-set-maintenance) nel sito della documentazione Fastly.

## Quali sono le differenze tra Adobe Commerce Cloud WAF e la soluzione WAF offerta da Fastly ai suoi clienti diretti?

La soluzione WAF venduta direttamente da Fastly è un&#39;offerta a pagamento che include set di regole più ampi e funzioni aggiuntive come la personalizzazione delle regole e la protezione da malware. La soluzione cloud WAF di Adobe Commerce include un sottoinsieme di regole mirate per l’applicazione Adobe Commerce e un solo set di regole per l’ambiente di produzione di ciascun cliente.

## Quali tipi di minacce alla sicurezza protegge WAF?

<table class="table-basic" style="width: 649px;">
<tbody>
<tr>
<th style="width: 145.5px; text-align: left;">Minaccia</th>
<th style="width: 497.5px; text-align: left;">Protezione WAF</th>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">Attacchi SQL injection</td>
<td style="width: 497.5px;">Sia il set di regole core di OWASP ModSecurity che il set di regole commerciali TrustWave includono filtri specifici per gli attacchi SQL injection e le relative varianti.</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">
<p>Iniezione intersito</p>
</td>
<td style="width: 497.5px;">Il set di regole di OWASP protegge dagli attacchi di iniezione intersito. Fastly sfrutta un meccanismo di punteggio per ogni richiesta di iniezione cross-site e altre minacce all’origine. Ogni richiesta viene valutata rispetto all’intero set di regole di base e verifica che il punteggio della richiesta sia inferiore a una soglia configurabile affinché possa essere superato.</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">Attacchi di forza bruta</td>
<td style="width: 497.5px;">Coperto dal set di regole di OWASP. Blocca inoltre l’attività di forza bruta utilizzando il codice VCL che riconosce origini, richieste o tentativi specifici di forza bruta o di superare i controlli di sicurezza prima che qualsiasi traffico raggiunga il datacenter di origine.</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">Attacchi di rete</td>
<td style="width: 497.5px;">Gli attacchi di rete, o attacchi mirati all'infrastruttura di rete, vengono gestiti automaticamente da Fastly. Fastly non passa il DNS all’origine e il traffico che non corrisponde a un profilo HTTP, HTTPS o DNS stretto viene scartato al margine della rete. I protocolli di controllo di targeting degli attacchi vengono difesi tramite l'autenticazione degli endpoint in tutta la rete. Inoltre, i protocolli di rete utilizzati all'interno della rete Fastly sono stati rafforzati per garantire che non possano essere utilizzati come mezzo di amplificazione o riflessione. I clienti sono responsabili della protezione contro gli attacchi che bypassano la rete Fastly sfruttando lo spazio di indirizzi IP Fastly Cache, pubblicato per i nostri clienti come componente del nostro servizio CDN. Si consiglia di non pubblicare lo spazio degli indirizzi IP di origine nel DNS pubblico per garantire che gli attacchi di bypass non possano utilizzare questi indirizzi come destinazioni.</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">Attacchi JavaScript injection</td>
<td style="width: 497.5px;">Le regole di WAF proteggono da codice JavaScript dannoso inserito nelle comunicazioni client con i servizi web. I pattern o i punteggi di exploit comuni vengono filtrati tramite WAF per garantire l’integrità del servizio di origine.</td>
</tr>
</tbody>
</table>

## Sono disponibili funzioni e funzionalità aggiuntive?

L&#39;offerta WAF di Adobe Commerce include la protezione contro le minacce OWASP Top 10 come parte dei requisiti PCI, supporto 24 ore su 24, 7 giorni su 7, inclusa la valutazione per falsi positivi, e aggiornamenti di versione. Le seguenti funzioni non sono supportate nell’offerta standard:

* limite di velocità
* personalizzazioni delle regole
* mitigazione bot
* protezione da malware

## In che modo le prestazioni del sito sono influenzate da WAF?

A ogni richiesta non memorizzata in cache viene introdotta una latenza stimata tra 1,5 millisecondi (ms) e 20 ms.

## I clienti possono creare e modificare blacklist IP per bloccare il traffico?

Sì, i clienti possono abilitare il blocco per paese e l’elenco di controllo di accesso (ACL) dall’interfaccia utente di amministrazione di Adobe Commerce sull’infrastruttura cloud. Utilizza queste funzioni nei casi in cui desideri bloccare l’accesso per i visitatori provenienti da paesi specifici o da determinati IP o intervalli IP. Se desideri che i visitatori bloccati visualizzino una pagina personalizzata invece di un codice di errore, puoi creare una pagina di errore personalizzata caricando HTML nel menu Configurazione rapida. Consulta [Creare una pagina di errore/manutenzione personalizzata](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=it) nella documentazione per gli sviluppatori.

## Dove è possibile controllare lo stato operativo del servizio WAF?

La disponibilità generale del servizio WAF è riportata nella [pagina Stato Fastly](https://status.fastly.com/). Non viene fornito alcun rapporto sulla disponibilità per il WAF dei singoli clienti.

## Adobe Commerce fornisce la gestione degli incidenti per il servizio WAF?

Al momento, la gestione degli incidenti non è disponibile.

## Adobe Commerce dispone di un Centro operativo per la sicurezza?

Sebbene Adobe Commerce non disponga di un Centro operativo per la sicurezza, disponiamo di un processo operativo per la sicurezza che ci consente di utilizzare le risorse giuste per rispondere in tempo reale agli incidenti di sicurezza. Offriamo anche supporto 24/7/365 follow-the-sun.

È inoltre possibile ricevere le notizie e gli aggiornamenti sulla sicurezza relativi ad Adobe Commerce dal [Centro sicurezza PC](https://helpx.adobe.com/it/security.html).

## Quale supporto è disponibile?

Il supporto WAF offre le seguenti risorse per aiutarti a mitigare l’impatto dei servizi dovuti a richieste indesiderate o dannose:

* Onboarding: abilitazione, configurazione iniziale e monitoraggio limitato dei servizi Fastly che supportano Adobe Commerce managed cloud WAF
* Tentativo di ricerca falso positivo continuo per risolvere le istanze in cui WAF blocca il traffico legittimo
* Configurazione di eventuali nuove regole standard introdotte come parte degli aggiornamenti della versione di WAF

Consulta i termini di [Cloud SLA](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Magento-Support-Services-Terms-and-Conditions.pdf) per ulteriori informazioni di supporto, tra cui definizioni di gravità, tempi di risposta, canali e disponibilità.

## Se WAF blocca il traffico legittimo o causa altri problemi, come posso ottenere aiuto?

[Invia un ticket di supporto](https://experienceleague.adobe.com/it/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) presso il [Centro assistenza Adobe Commerce](https://support.magento.com). Indica che il ticket è correlato al servizio WAF e includi l’identificatore della richiesta (ID) bloccato.

Il sistema di ticket del supporto Adobe Commerce tiene traccia delle comunicazioni tra i tecnici del supporto e il personale di un cliente. Questo sistema fornisce una trascrizione con marca temporale delle comunicazioni e invia e-mail al cliente e al personale di Adobe Commerce man mano che i biglietti vengono aggiornati.

Per tutti gli Incidenti inviati online, la ricevuta verrà confermata tramite il sistema di ticket del Centro assistenza clienti di Adobe Commerce. Dopo aver ricevuto un caso presentato correttamente, i servizi di supporto ricevono una priorità in base ai livelli di priorità sopra indicati.

Nella tabella seguente sono riepilogati i canali di supporto e la disponibilità per il supporto WAF:

<table class="table-basic">
<tbody>
<tr>
<th>Offerta di supporto</th>
<th>Dettagli</th>
</tr>
<tr>
<td>Guida self-service online</td>
<td>Accesso illimitato</td>
</tr>
<tr>
<td>Disponibilità per i rapporti sugli incidenti</td>
<td>24/7</td>
</tr>
<tr>
<td>Portale web</td>
<td>Disponibile tramite Zendesk</td>
</tr>
<tr>
<td>Escalation di emergenza*</td>
<td>Consulta l'articolo <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/adobe-commerce-p1-notification-hotline.html?lang=it">Hotline per le notifiche Adobe Commerce P1</a> per i numeri degli Stati Uniti e internazionali.</td>
</tr>
</tbody>
</table>

*\* La linea telefonica gratuita del Supporto Adobe Commerce è riservata solo agli incidenti con priorità 1. Le chiamate non prioritarie 1 rallenteranno la risposta complessiva ai problemi*

## Come vengono valutati i falsi positivi?

Abbiamo un processo di valutazione falso positivo (disponibile 24 ore su 24, 7 giorni su 7) per affrontare e risolvere rapidamente le istanze in cui richieste legittime hanno attivato una regola WAF. I falsi positivi sono trattati come problemi con priorità 1. Come azione predefinita, il nostro team di supporto può aggiornare immediatamente i criteri di WAF per disabilitare la regola che ha attivato l’evento di blocco e consentire alla richiesta legittima di passare attraverso WAF.

## Cosa succede se il traffico verso la sezione amministratore del sito di Adobe Commerce sull’infrastruttura cloud attiva le regole di WAF? Il supporto Adobe Commerce risolverà i problemi con il traffico amministratore bloccato?

Sì, il traffico di amministrazione bloccato viene trattato come un problema di priorità 1.
