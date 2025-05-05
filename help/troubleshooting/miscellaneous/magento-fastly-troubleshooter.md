---
title: Risoluzione dei problemi Fastly di Adobe Commerce
description: Questo strumento di risoluzione rapida dei problemi per gli utenti di Adobe Commerce ti guiderà verso le soluzioni, in base alla tua risposta sui sintomi visualizzati. Fai clic sulle domande per visualizzare le opzioni o risposte successive.
exl-id: c5c51b89-5a7d-49ba-a0ee-7abbaf78fdad
feature: Support, Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# Risoluzione dei problemi Fastly di Adobe Commerce

Questo strumento di risoluzione rapida dei problemi per gli utenti di Adobe Commerce ti guiderà verso le soluzioni, in base alla tua risposta sui sintomi visualizzati. Fai clic sulle domande per visualizzare le opzioni o risposte successive.

## Passaggio 1: verificare il servizio Fastly {#step-1}

+++**Il cliente segnala un problema relativo a Fastly. Il servizio Fastly è inattivo?**

a. SÌ - Controlla [Stato servizio rapido](https://status.fastly.com/) e [invia un ticket di supporto Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO - Procedi al [passaggio 2](#step-2).

+++

## Passaggio 2: controllare il file di configurazione VCL {#step-2}

+++**Si sono verificati errori durante l&#39;esecuzione del test di back-end?**

Esegui l&#39;URL del progetto tramite [Tester back-end - Fastly](https://magento-tester.global.ssl.fastly.net/magento-tester/). Mostra la versione del file di configurazione VCL, se la pagina è memorizzabile in cache, la versione del modulo Fastly e altre informazioni utili per la risoluzione dei problemi. Ha degli errori?

a. SÌ - Viene visualizzato il messaggio _La versione del plug-in VCL è obsoleta. Ricarica._ Per risolvere l&#39;errore, fare riferimento a [Errore rapido: la versione VCL del plug-in è obsoleta. Ricarica](/help/troubleshooting/miscellaneous/fastly-error-plugin-vcl-version-is-outdated-please-re-upload.md).\
b. NO - [Passaggio 3](#step-3).

+++

## Passaggio 3: verifica la presenza di un errore di ottimizzazione immagine {#step-3}

+++**Errore di ottimizzazione immagine?**

a. YES - [Errore durante l&#39;abilitazione dell&#39;ottimizzazione immagine](/help/troubleshooting/miscellaneous/error-enabling-image-optimization-in-magento-commerce.md).\
b. NO - Controllare il DNS eseguendo il comando in CLI/terminale: `dig [your website.com] + short`. Procedi al [passaggio 4](#step-4).

+++

## Passaggio 4: verifica del DNS {#step-4}

+++**Cosa succede quando esegui `dig`?**

`dig` ha restituito un record che punta a prod.magentocloud.map.fastly.net o a uno dei seguenti indirizzi IP (vedi [Aggiornare la configurazione DNS con le impostazioni di produzione](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/launch/checklist#update-dns-configuration-with-production-settings) nella documentazione per gli sviluppatori):

* 151 101 124
* 151 101 65 124
* 151 101 129 124
* 151 101 193 124

a. SÌ - Il problema non è relativo al DNS. Procedi al [passaggio 5](#step-5).\
b. NO - Il problema è probabilmente correlato al DNS. Il cliente deve [controllare la configurazione DNS](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/launch/checklist#update-dns-configuration-with-production-settings) o contattare il provider DNS per ulteriori informazioni.

+++

## Passaggio 5 - Conferma della connessione {#step-5}

+++**Viene restituito un messaggio &quot;Connessione non sicura&quot; o &quot;Non sicura&quot; durante l&#39;esecuzione di `curl -svo /dev/null "https://website.com"` nell&#39;interfaccia della riga di comando/terminale?**

a. SÌ - È probabile che sia stato rilasciato un certificato. Visita il sito web in un browser, seleziona l’icona a forma di lucchetto e cerca la scadenza del certificato. Procedi al [passaggio 6](#step-6).\
b. NO - Visita [http://fastly-debug.com](https://www.fastly-debug.com/) e condividi queste informazioni in un [ticket di supporto Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Passaggio 6: verifica di disporre di un certificato TSL valido {#step-6}

+++**Il certificato è scaduto?**

a. SÌ - È necessario rinnovare il certificato TLS con l’autorità di certificazione (CA).\
b. NO - È possibile che non si disponga di un certificato. Se disponi di Adobe Commerce, ti consigliamo di acquistare un certificato TLS. Se ti trovi su Adobe Commerce nell’infrastruttura cloud, puoi disporre di un certificato SSL/TLS crittografato con convalida di dominio per gestire il traffico HTTPS protetto da Fastly. Consulta [effettuare il provisioning dei certificati SSL/TLS](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#provision-ssltls-certificates) nella documentazione per gli sviluppatori.

+++

[Torna al passaggio 1](#step-1)
