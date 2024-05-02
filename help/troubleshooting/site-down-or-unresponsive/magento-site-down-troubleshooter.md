---
title: Risoluzione dei problemi relativi al sito Adobe Commerce inattivo
description: Fare clic su ogni domanda per visualizzare i dettagli delle risposte in ogni passaggio dello strumento di risoluzione dei problemi.
exl-id: 10a2313e-cc82-4ffc-9247-624884f3e165
feature: Support
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 0%

---

# Risoluzione dei problemi relativi al sito Adobe Commerce inattivo

Fare clic su ogni domanda per visualizzare i dettagli delle risposte in ogni passaggio dello strumento di risoluzione dei problemi.

## Passaggio 1 {#step-1}

+++**Does <https://status.adobe.com> mostrare dei problemi?**

a. SÌ - Se è stato selezionato [Stato Magento Adobe](https://status.adobe.com/products/3350) e mostrava un problema, apri un [Ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) per ulteriori indagini.\
b. NO - Se è stato selezionato [Stato Magento Adobe](https://status.adobe.com/products/3350) e non ha mostrato alcun problema, procedi con [Passaggio 2](#step-2).

+++

## Passaggio 2 {#step-2}

+++**http://status.fastly.com mostra qualche problema?**

a. SÌ - Se è stato selezionato [Stato veloce](https://status.fastly.com/) e mostrava un problema, apri un [Ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) per ulteriori indagini.\
b. NO - Se è stato selezionato [Stato veloce](https://status.fastly.com/) e non ha mostrato alcun problema, procedi con [Passaggio 3](#step-3).

+++

## Passaggio 3 {#step-3}

+++**Controlla il tuo sito web in un browser web. Ricevi un codice 200 (OK)?**

Per controllare i codici di errore in **Firefox**: fai clic su **Apri menu** icona > **Web Developer** > **Attiva/Disattiva strumenti** > **Rete** scheda > **Tutti** filter > **Stato** colonna. Per controllare i codici di errore in **Chrome**: fai clic su **Apri menu** icona > **Altri strumenti** > **Strumenti per sviluppatori** > **Rete** scheda > **Tutti** filter > **Stato** colonna.

a. SÌ - Apri una [Ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) per ulteriori indagini.\
b. NO - Procedi a [Passaggio 4](#step-4).

+++

## Passaggio 4 {#step-4}

+++**Quale codice di errore del sito Web è stato ricevuto?**

a. Codice errore 500 - Registro di controllo `/var/log/platform/`. Se questi dati non presentano il problema, puoi aprire una [Ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) e includere le informazioni sulla risoluzione dei problemi disponibili per ulteriori indagini.

b. Codice errore 503 - Registro di controllo `var/reports`. Se questi dati non presentano il problema, puoi aprire una [Ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) e includere le informazioni sulla risoluzione dei problemi disponibili per ulteriori indagini.

c. Codice di errore 404 - Eseguire la seguente query: `SELECT f.flag_data->>'$.current_version' as flag_version, (su.id IS NOT NULL) as update_exists FROM flag f LEFT JOIN staging_update su ON su.id = f.flag_data->>'$.current_version' WHERE flag_code = 'staging';` Se la query restituisce una tabella, dove `update_exists` valore è &quot;0&quot;, fare riferimento al [Errore 404 su tutte le pagine, vetrina e amministratore, a causa di un problema di staging del contenuto](/help/troubleshooting/site-down-or-unresponsive/error-404-on-all-pages-due-to-content-staging-issue.md) articolo. In tutti gli altri casi procedere come segue: [Passaggio 5](#step-5).

d. Altri codici di errore - Procedi a [Passaggio 5](#step-5).

+++

## Passaggio 5 {#step-5}

+++**Il sito è lento o presenta un carico server elevato, un carico CPU elevato, un&#39;elaborazione delle richieste lenta o interruzioni in MySQL o Redis?**

a. SÌ - Procedere con i passaggi per [Controllo degli attacchi DDOS da CLI](/help/troubleshooting/miscellaneous/checking-for-ddos-attack-from-cli.md).\
b. NO - Registri di verifica di `/var/log/exception.log` e `/var/log/deploy.log`, e se questi dati non ti presentano il problema, procedi come segue: [Passaggio 6](#step-6).

+++

## Passaggio 6 {#step-6}

+++**Si sono verificati errori di distribuzione o errori di distribuzione?**

a. SÌ - Procedere come segue [Passaggio 13](#step-13).\
b. NO - Procedi a [Passaggio 7](#step-7).

+++

## Passaggio 7 {#step-7}

+++**Ha degli errori Elasticsearch?**

a. SÌ - Procedere con i passaggi per [Elasticsearch di verifica](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/configure-magento.html).\
b. NO - Procedi a [Passaggio 8](#step-8).

+++

## Passaggio 8 {#step-8}

+++**Il database MySQL conteneva query lente o non corrette?**

a. SÌ - Procedere con [Verifica di query e processi lenti che richiedono troppo tempo in MySQL](/help/troubleshooting/database/checking-slow-queries-and-processes-mysql.md) e controllare la struttura delle query in questo [Esercitazione sulle query MySQL](https://dev.mysql.com/doc/refman/5.5/en/entering-queries.html).\
b. NO - Procedi a [Passaggio 9](#step-9).

+++

## Passaggio 9 {#step-9}

+++**Il contenuto statico non è disponibile?**

a. SÌ - Procedere con la consultazione del [Verifica del contenuto statico](https://support.magento.com/hc/en-us/articles/360031624091) articolo.\
b. NO - Procedi a [Passaggio 10](#step-10).

+++

## Passaggio 10 {#step-10}

+++**Nei registri vengono visualizzati gli errori irreversibili PHP?**

a. SÌ - Procedere con la consultazione [Errori irreversibili PHP comuni e soluzioni](/help/troubleshooting/miscellaneous/common-php-fatal-errors-and-solutions.md).\
b. NO - Procedi a [Passaggio 11](#step-11).

+++

## Passaggio 11 {#step-11}

+++**Stai vedendo degli errori Redis?**

a. SÌ - Procedere con i passaggi per [verifica che Redis sia in esecuzione](https://devdocs.magento.com/guides/v2.3/config-guide/redis/redis-session.html#redis-verify) e per [Risoluzione dei problemi di Redis](https://redis.io/topics/problems).\
b. NO - Procedi a [Passaggio 12](#step-12).

+++

## Passaggio 12 {#step-12}

+++**Vengono visualizzati errori dell&#39;indicizzatore?**

a. SÌ - Se l’indice è bloccato da un altro processo, consultare [Indice bloccato da un altro processo](/help/troubleshooting/miscellaneous/index-is-locked-by-another-process.md). Se si verificano altri errori dell&#39;indicizzatore, aprire un [Ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) per ulteriori indagini.\
b. NO - Apri un [Ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) per ulteriori indagini.

+++

## Passaggio 13 {#step-13}

+++**Si sono verificati problemi con i moduli personalizzati?**

a. SÌ - Consultare [Guida generale alla risoluzione dei problemi dei moduli personalizzati](/help/troubleshooting/miscellaneous/general-custom-module-troubleshooting-help.md).\
b. NO - Procedi a [Passaggio 14](#step-14).

+++

## Passaggio 14 {#step-14}

+++**Hai degli errori post-hook?**

a. YES - Procedere con la verifica dell&#39;errore MySQL in questo [Riferimento messaggio di errore di MySQL Server](https://dev.mysql.com/doc/mysql-errors/5.7/en/server-error-reference.html).\
b. NO - Procedi a [Passaggio 15](#step-15).

+++

## Passaggio 15 {#step-15}

+++**Si sono verificati problemi con le patch del compositore?**

a. SÌ - Procedere alla consultazione [L’applicazione di una patch blocca il sito](/help/troubleshooting/site-down-or-unresponsive/applying-a-patch-takes-your-site-down.md).\
b. NO - Procedi a [Passaggio 16](#step-16).

+++

## Passaggio 16 {#step-16}

+++**Si sono verificati errori nel database SQL?**

a. YES - Procedere con la verifica dell&#39;errore MySQL in questo [Riferimento messaggio di errore di MySQL Server](https://dev.mysql.com/doc/mysql-errors/5.7/en/server-error-reference.html).\
b. NO - Procedi a [Passaggio 17](#step-17).

+++

## Passaggio 17 {#step-17}

+++**Si dispone di blocchi inattivi del database MySQL o di un database MySQL che non risponde?**

a. YES - Procedere con la verifica dei blocchi inattivi MySQL in questo [Deadlock in MySQL](/help/troubleshooting/database/deadlocks-in-mysql.md) articolo.\
b. NO - Apri un [Ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) per ulteriori indagini.

+++

[Torna al passaggio 1](#step-1)

Clic [QUI](/help/troubleshooting/site-down-or-unresponsive/site-down-troubleshooting-diagram.md) per visualizzare il diagramma di flusso per la risoluzione dei problemi del sito.
