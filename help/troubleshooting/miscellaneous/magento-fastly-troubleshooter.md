---
title: Risoluzione dei problemi Fastly di Adobe Commerce
description: Questo strumento di risoluzione rapida dei problemi per gli utenti di Adobe Commerce ti guiderà verso le soluzioni, in base alla tua risposta sui sintomi visualizzati. Fai clic sulle domande per visualizzare le opzioni o risposte successive.
exl-id: c5c51b89-5a7d-49ba-a0ee-7abbaf78fdad
feature: Support, Services
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# Risoluzione dei problemi Fastly di Adobe Commerce

Questo strumento di risoluzione rapida dei problemi per gli utenti di Adobe Commerce ti guiderà verso le soluzioni, in base alla tua risposta sui sintomi visualizzati. Fai clic sulle domande per visualizzare le opzioni o risposte successive.

## Passaggio 1: verificare il servizio Fastly {#step-1}

+++**Il cliente segnala un problema relativo a Fastly. Il servizio Fastly è inattivo?**

a. SÌ - Spunta [Stato servizio rapido](https://status.fastly.com/), e [invia un ticket di supporto Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO - Procedi a [Passaggio 2](#step-2).

+++

## Passaggio 2: controllare il file di configurazione VCL {#step-2}

+++**Si sono verificati errori durante l&#39;esecuzione del test back-end?**

Eseguire l’URL del progetto tramite [Tester back-end - Fastly](https://magento-tester.global.ssl.fastly.net/magento-tester/). Mostra la versione del file di configurazione VCL, se la pagina è memorizzabile in cache, la versione del modulo Fastly e altre informazioni utili per la risoluzione dei problemi. Ha degli errori?

a. SÌ - Hai ricevuto il messaggio _La versione del plug-in VCL è obsoleta. Ricarica._ Per la soluzione a questo errore, fare riferimento a [Errore rapido: versione VCL del plug-in obsoleta. Ricarica](/help/troubleshooting/miscellaneous/fastly-error-plugin-vcl-version-is-outdated-please-re-upload.md).\
b. N. - [Passaggio 3](#step-3).

+++

## Passaggio 3: verifica la presenza di un errore di ottimizzazione immagine {#step-3}

+++**Errore di ottimizzazione immagine?**

a. SÌ [Errore durante l&#39;abilitazione dell&#39;ottimizzazione immagine](/help/troubleshooting/miscellaneous/error-enabling-image-optimization-in-magento-commerce.md).\
b. NO - Controllare il DNS eseguendo il comando in CLI/terminale: `dig [your website.com] + short`. Procedi a [Passaggio 4](#step-4).

+++

## Passaggio 4: verifica del DNS {#step-4}

+++**Cosa succede quando esegui `dig`?**

Quando hai corso `dig` ha restituito un record che punta a prod.magentocloud.map.fastly.net o a uno dei seguenti indirizzi IP (vedi [Aggiorna configurazione DNS con impostazione di produzione](https://devdocs.magento.com/cloud/live/site-launch-checklist.html#dns) nella documentazione per gli sviluppatori):

* 151 101 124
* 151 101 65 124
* 151 101 129 124
* 151 101 193 124

a. SÌ - Il problema non è relativo al DNS. Procedi a [Passaggio 5](#step-5).\
b. NO - Il problema è probabilmente correlato al DNS. Il cliente deve [verifica configurazione DNS](https://devdocs.magento.com/cloud/live/site-launch-checklist.html#dns "https://devdocs.magento.com/cloud/live/site-launch-checklist.html#dns") o contatta il provider DNS per ulteriori informazioni.

+++

## Passaggio 5 - Conferma della connessione {#step-5}

+++**Viene restituito il messaggio &quot;Connessione non sicura&quot; o &quot;Non sicura&quot; durante l&#39;esecuzione `curl -svo /dev/null "https://website.com"` nella CLI/terminale?**

a. SÌ - È probabile che sia stato rilasciato un certificato. Visita il sito web in un browser, seleziona l’icona a forma di lucchetto e cerca la scadenza del certificato. Procedi a [Passaggio 6](#step-6).\
b. NO - Visita [http://fastly-debug.com](https://www.fastly-debug.com/) e condividere queste informazioni in un [Ticket di supporto Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Passaggio 6: verifica di disporre di un certificato TSL valido {#step-6}

+++**Il certificato è scaduto?**

a. SÌ - È necessario rinnovare il certificato TLS con l’autorità di certificazione (CA).\
b. NO - È possibile che non si disponga di un certificato. Se disponi di Adobe Commerce, ti consigliamo di acquistare un certificato TLS. Se ti trovi su Adobe Commerce nell’infrastruttura cloud, puoi disporre di un certificato SSL/TLS crittografato con convalida di dominio per gestire il traffico HTTPS protetto da Fastly. Consulta [provisioning dei certificati SSL/TLS](https://devdocs.magento.com/cloud/cdn/configure-fastly.html#provision-ssltls-certificates) nella documentazione per gli sviluppatori.

+++

[Torna al passaggio 1](#step-1)
