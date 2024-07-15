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

+++**In <https://status.adobe.com> sono visualizzati problemi?**

a. SÌ - Se hai selezionato [Stato Magento Adobe](https://status.adobe.com/products/3350) e si è verificato un problema, apri un [ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) per ulteriori indagini.\
b. NO - Se hai selezionato [Stato Magento Adobe](https://status.adobe.com/products/3350) e non è stato rilevato alcun problema, procedi al [passaggio 2](#step-2).

+++

## Passaggio 2 {#step-2}

+++**http://status.fastly.com mostra problemi?**

a. SÌ - Se hai selezionato [Fastly Status](https://status.fastly.com/) e si è verificato un problema, apri un [Ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) per ulteriori indagini.\
b. NO - Se è stato selezionato [Fastly Status](https://status.fastly.com/) e il problema non è stato visualizzato, passare al [Passaggio 3](#step-3).

+++

## Passaggio 3 {#step-3}

+++**Controlla il tuo sito Web in un browser Web. Ottieni un codice 200 (OK)?**

Per verificare i codici di errore in **Firefox**: fare clic sull&#39;icona **Apri menu** > **Web Developer** > **Attiva/disattiva strumenti** > **Rete** scheda > **Tutti** filtro > **Stato** colonna. Per verificare i codici di errore in **Chrome**: fare clic sull&#39;icona **Apri menu** > **Altri strumenti** > **Strumenti per sviluppatori** > **Scheda Rete** > **Tutti** filtro > **Colonna Stato**.

a. SÌ - Apri un [ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) per ulteriori indagini.\
b. NO - Procedi al [passaggio 4](#step-4).

+++

## Passaggio 4 {#step-4}

+++**Quale codice di errore del sito Web è stato ricevuto?**

a. Codice errore 500 - Registro di controllo di `/var/log/platform/`. Se questi dati non presentano il problema, è possibile aprire un [ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) e includere le informazioni sulla risoluzione dei problemi disponibili per ulteriori indagini.

b. Codice errore 503 - Registro di controllo di `var/reports`. Se questi dati non presentano il problema, è possibile aprire un [ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) e includere le informazioni sulla risoluzione dei problemi disponibili per ulteriori indagini.

c. Codice di errore 404 - Eseguire la seguente query: `SELECT f.flag_data->>'$.current_version' as flag_version, (su.id IS NOT NULL) as update_exists FROM flag f LEFT JOIN staging_update su ON su.id = f.flag_data->>'$.current_version' WHERE flag_code = 'staging';` Se la query restituisce una tabella, dove il valore `update_exists` è &quot;0&quot;, fare riferimento all&#39;articolo [Errore 404 in tutte le pagine, vetrina e amministratore, a causa di un problema di gestione temporanea del contenuto](/help/troubleshooting/site-down-or-unresponsive/error-404-on-all-pages-due-to-content-staging-issue.md). In tutti gli altri casi procedere al [passaggio 5](#step-5).

d. Altri codici di errore - Procedere con [Passaggio 5](#step-5).

+++

## Passaggio 5 {#step-5}

+++**Il tuo sito è lento, il carico del server è elevato, il carico della CPU è elevato, l&#39;elaborazione delle richieste è lenta o le interruzioni in MySQL o Redis?**

a. YES - Procedere con i passaggi per [Verifica degli attacchi DDOS da CLI](/help/troubleshooting/miscellaneous/checking-for-ddos-attack-from-cli.md).\
b. NO - Controllare i registri di `/var/log/exception.log` e `/var/log/deploy.log` e se questi dati non presentano il problema, passare al [passaggio 6](#step-6).

+++

## Passaggio 6 {#step-6}

+++**Si sono verificati errori di distribuzione o errori di distribuzione?**

a. SÌ - Procedere al [passaggio 13](#step-13).\
b. NO - Procedi al [passaggio 7](#step-7).

+++

## Passaggio 7 {#step-7}

+++**Si sono verificati errori di Elasticsearch?**

a. SÌ - Procedi con i passaggi per [verificare l&#39;Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/configure-magento.html).\
b. NO - Procedi al [passaggio 8](#step-8).

+++

## Passaggio 8 {#step-8}

+++**Il database MySQL conteneva query lente o non corrette?**

a. SÌ - Procedere con [Verifica delle query lente e dei processi che richiedono troppo tempo in MySQL](/help/troubleshooting/database/checking-slow-queries-and-processes-mysql.md) e verifica la struttura delle query in questa [esercitazione sulle query MySQL](https://dev.mysql.com/doc/refman/5.5/en/entering-queries.html).\
b. NO - Procedi al [passaggio 9](#step-9).

+++

## Passaggio 9 {#step-9}

+++**Il contenuto statico non è disponibile?**

a. SÌ - Procedi consultando l&#39;articolo [Verifica del contenuto statico](https://support.magento.com/hc/en-us/articles/360031624091).\
b. NO - Procedi al [passaggio 10](#step-10).

+++

## Passaggio 10 {#step-10}

+++**Nei registri sono presenti errori irreversibili PHP?**

a. SÌ - Procedere con la consulenza [Errori irreversibili PHP comuni](/help/troubleshooting/miscellaneous/common-php-fatal-errors-and-solutions.md).\
b. NO - Procedi al [passaggio 11](#step-11).

+++

## Passaggio 11 {#step-11}

+++**Sono presenti errori Redis?**

a. SÌ - Procedi con i passaggi per [verificare che Redis sia in esecuzione](https://devdocs.magento.com/guides/v2.3/config-guide/redis/redis-session.html#redis-verify) e per [la risoluzione dei problemi Redis](https://redis.io/topics/problems).\
b. NO - Procedere al [passaggio 12](#step-12).

+++

## Passaggio 12 {#step-12}

+++**Sono presenti errori dell&#39;indicizzatore?**

a. SÌ - Se l&#39;indice è bloccato da un altro processo, consultare [L&#39;indice è bloccato da un altro processo](/help/troubleshooting/miscellaneous/index-is-locked-by-another-process.md). Se si verificano altri errori dell&#39;indicizzatore, aprire un [ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) per ulteriori indagini.\
b. NO - Apri un [ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) per ulteriori indagini.

+++

## Passaggio 13 {#step-13}

+++**Si sono verificati problemi con i moduli personalizzati?**

a. SÌ - Consulta [Guida generale alla risoluzione dei problemi dei moduli personalizzati](/help/troubleshooting/miscellaneous/general-custom-module-troubleshooting-help.md).\
b. NO - Procedi al [passaggio 14](#step-14).

+++

## Passaggio 14 {#step-14}

+++**Si sono verificati errori post-hook?**

a. YES - Procedere con la verifica dell&#39;errore MySQL in questo [Riferimento del messaggio di errore del server MySQL](https://dev.mysql.com/doc/mysql-errors/5.7/en/server-error-reference.html).\
b. NO - Procedi al [passaggio 15](#step-15).

+++

## Passaggio 15 {#step-15}

+++**Si sono verificati problemi con le patch del compositore?**

a. SÌ - Procedere con la consulenza [L&#39;applicazione di una patch provoca la chiusura del sito](/help/troubleshooting/site-down-or-unresponsive/applying-a-patch-takes-your-site-down.md).\
b. NO - Procedi al [passaggio 16](#step-16).

+++

## Passaggio 16 {#step-16}

+++**Si sono verificati errori nel database SQL?**

a. YES - Procedere con la verifica dell&#39;errore MySQL in questo [Riferimento del messaggio di errore del server MySQL](https://dev.mysql.com/doc/mysql-errors/5.7/en/server-error-reference.html).\
b. NO - Procedi al [passaggio 17](#step-17).

+++

## Passaggio 17 {#step-17}

+++**Il database MySQL è bloccato o non risponde?**

a. YES - Procedere con la verifica dei blocchi inattivi MySQL in questo articolo [Deadlocks in MySQL](/help/troubleshooting/database/deadlocks-in-mysql.md).\
b. NO - Apri un [ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) per ulteriori indagini.

+++

[Torna al passaggio 1](#step-1)

Fai clic [QUI](/help/troubleshooting/site-down-or-unresponsive/site-down-troubleshooting-diagram.md) per visualizzare il diagramma di flusso per la risoluzione dei problemi del sito.
