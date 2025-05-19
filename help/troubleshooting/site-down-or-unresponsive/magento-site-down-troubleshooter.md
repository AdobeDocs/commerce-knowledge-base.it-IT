---
title: Risoluzione dei problemi relativi al sito Adobe Commerce inattivo
description: Fare clic su ogni domanda per visualizzare i dettagli delle risposte in ogni passaggio dello strumento di risoluzione dei problemi.
exl-id: 10a2313e-cc82-4ffc-9247-624884f3e165
feature: Support
role: Developer
source-git-commit: 66ff85507ec91def7aa836469b243c32c4e161cc
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 0%

---

# Risoluzione dei problemi relativi al sito Adobe Commerce inattivo

Fare clic su ogni domanda per visualizzare i dettagli delle risposte in ogni passaggio dello strumento di risoluzione dei problemi.

>[!NOTE]
>
>Prima di creare un [ticket di supporto](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide?lang=en#support-cases), controlla la pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) per verificare se il problema è già elencato.

## Passaggio 1 {#step-1}

+++**In <https://status.adobe.com> sono visualizzati problemi?**

a. SÌ - Se è stato selezionato [Stato Adobe Commerce](https://status.adobe.com/cloud/experience_cloud) e si è verificato un problema, aprire un [ticket di supporto](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) per ulteriori informazioni.\
b. NO - Se hai selezionato [Stato Adobe Commerce](https://status.adobe.com/cloud/experience_cloud) e il problema non è stato rilevato, procedi al [Passaggio 2](#step-2).

+++

## Passaggio 2 {#step-2}

+++**http://status.fastly.com mostra problemi?**

a. SÌ - Se è stato selezionato [[!DNL Fastly] Stato](https://status.fastly.com/) e si è verificato un problema, aprire [Ticket di supporto](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) per ulteriori informazioni.\
b. NO - Se hai selezionato [[!DNL Fastly] Stato](https://status.fastly.com/) e il problema non è stato visualizzato, procedi al [Passaggio 3](#step-3).

+++

## Passaggio 3 {#step-3}

+++**Controlla il tuo sito Web in un browser Web. Ottieni un codice 200 (OK)?**

Per verificare i codici di errore in **Firefox**: fare clic sull&#39;icona **Apri menu** > **Web Developer** > **Attiva/disattiva strumenti** > **Rete** scheda > **Tutti** filtro > **Stato** colonna. Per verificare i codici di errore in **Chrome**: fare clic sull&#39;icona **Apri menu** > **Altri strumenti** > **Strumenti per sviluppatori** > **Scheda Rete** > **Tutti** filtro > **Colonna Stato**.

a. SÌ - Apri un [ticket di supporto](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) per ulteriori indagini.\
b. NO - Procedi al [passaggio 4](#step-4).

+++

## Passaggio 4 {#step-4}

+++**Quale codice di errore del sito Web è stato ricevuto?**

a. Codice errore 500 - Registro di controllo di `/var/log/platform/`. Se questi dati non presentano il problema, è possibile aprire un [ticket di supporto](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) e includere le informazioni sulla risoluzione dei problemi disponibili per ulteriori indagini.

b. Codice errore 503 - Registro di controllo di `var/reports`. Se questi dati non presentano il problema, è possibile aprire un [ticket di supporto](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) e includere le informazioni sulla risoluzione dei problemi disponibili per ulteriori indagini.

c. Codice di errore 404 - Eseguire la seguente query: `SELECT f.flag_data->>'$.current_version' as flag_version, (su.id IS NOT NULL) as update_exists FROM flag f LEFT JOIN staging_update su ON su.id = f.flag_data->>'$.current_version' WHERE flag_code = 'staging';` Se la query restituisce una tabella, dove il valore `update_exists` è &quot;0&quot;, fare riferimento all&#39;articolo [Errore 404 in tutte le pagine, vetrina e amministratore, a causa di un problema di gestione temporanea del contenuto](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/error-404-on-all-pages-due-to-content-staging-issue). In tutti gli altri casi procedere al [passaggio 5](#step-5).

d. Altri codici di errore - Procedere con [Passaggio 5](#step-5).

+++

## Passaggio 5 {#step-5}

+++**Il tuo sito è lento, il carico del server è elevato, il caricamento del CPU è elevato, l&#39;elaborazione delle richieste è lenta o le interruzioni si verificano in [!DNL MySQL] o Redis?**

a. YES - Procedere con i passaggi per [Verifica degli attacchi DDOS da CLI](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-for-ddos-attack-from-cli).\
b. NO - Controllare i registri di `/var/log/exception.log` e `/var/log/deploy.log` e se questi dati non presentano il problema, passare al [passaggio 6](#step-6).

+++

## Passaggio 6 {#step-6}

+++**Si sono verificati errori di distribuzione o errori di distribuzione?**

a. SÌ - Procedere al [passaggio 13](#step-13).\
b. NO - Procedi al [passaggio 7](#step-7).

+++

## Passaggio 7 {#step-7}

+++**Si sono verificati errori in Elasticsearch?**

a. SÌ - Procedi con i passaggi per [controllare Elasticsearch](https://experienceleague.adobe.com/it/docs/commerce-operations/configuration-guide/search/configure-search-engine).
b. NO - Procedi al [passaggio 8](#step-8).

+++

## Passaggio 8 {#step-8}

+++**Il database [!DNL MySQL] conteneva query lente o non corrette?**

a. SÌ - Procedi con [Verifica delle query lente e dei processi che richiedono troppo tempo nell&#39; [!DNL MySQL]](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/troubleshooting/database/checking-slow-queries-and-processes-mysql) and checking your query structure in this [[!DNL MySQL] esercitazione sulle query](https://dev.mysql.com/doc/refman/5.5/en/entering-queries.html).\
b. NO - Procedi al [passaggio 9](#step-9).

+++

## Passaggio 9 {#step-9}

+++**Il contenuto statico non è disponibile?**

a. SÌ - Procedi consultando l&#39;articolo [Verifica del contenuto statico](https://experienceleague.adobe.com/it/docs/commerce-operations/implementation-playbook/best-practices/development/static-content-deployment).\
b. NO - Procedi al [passaggio 10](#step-10).

+++

## Passaggio 10 {#step-10}

+++**Nei registri sono presenti errori irreversibili PHP?**

a. SÌ - Procedere con la consulenza [Errori irreversibili PHP comuni](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/common-php-fatal-errors-and-solutions).\
b. NO - Procedi al [passaggio 11](#step-11).

+++

## Passaggio 11 {#step-11}

+++**Sono presenti errori Redis?**

a. SÌ - Procedi con i passaggi per [verificare [!DNL Redis] che sia in esecuzione](https://experienceleague.adobe.com/it/docs/commerce-operations/configuration-guide/cache/redis/redis-session#verify-redis-connection) e per [[!DNL Redis] la risoluzione dei problemi](https://redis.io/topics/problems).\
b. NO - Procedere al [passaggio 12](#step-12).

+++

## Passaggio 12 {#step-12}

+++**Sono presenti errori dell&#39;indicizzatore?**

a. SÌ - Se l&#39;indice è bloccato da un altro processo, consultare [L&#39;indice è bloccato da un altro processo](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/index-is-locked-by-another-process). Se si verificano altri errori dell&#39;indicizzatore, aprire un [ticket di supporto](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) per ulteriori indagini.\
b. NO - Apri un [ticket di supporto](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) per ulteriori indagini.

+++

## Passaggio 13 {#step-13}

+++**Si sono verificati problemi con i moduli personalizzati?**

a. SÌ - Consulta [Guida generale alla risoluzione dei problemi dei moduli personalizzati](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/general-custom-module-troubleshooting-help).\
b. NO - Procedi al [passaggio 14](#step-14).

+++

## Passaggio 14 {#step-14}

+++**Si sono verificati errori post-hook?**

a. SÌ - Procedi con la verifica dell&#39;errore [!DNL MySQL] in questo [[!DNL MySQL] riferimento del messaggio di errore del server](https://dev.mysql.com/doc/mysql-errors/5.7/en/server-error-reference.html).\
b. NO - Procedi al [passaggio 15](#step-15).

+++

## Passaggio 15 {#step-15}

+++**Si sono verificati problemi con le patch del compositore?**

a. SÌ - Procedere con la consulenza [L&#39;applicazione di una patch provoca la chiusura del sito](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/applying-a-patch-takes-your-site-down).\
b. NO - Procedi al [passaggio 16](#step-16).

+++

## Passaggio 16 {#step-16}

+++**Si sono verificati errori nel database SQL?**

a. SÌ - Procedi con la verifica dell&#39;errore [!DNL MySQL] in questo [[!DNL MySQL] riferimento del messaggio di errore del server](https://dev.mysql.com/doc/mysql-errors/5.7/en/server-error-reference.html).\
b. NO - Procedi al [passaggio 17](#step-17).

+++

## Passaggio 17 {#step-17}

+++**Sono presenti [!DNL MySQL] blocchi inattivi del database o un database [!DNL MySQL] non reattivo?**

a. SÌ - Procedi con la verifica di [!DNL MySQL] deadlock in questo articolo [Deadlocks in [!DNL MySQL]](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/troubleshooting/database/deadlocks-in-mysql).\
b. NO - Apri un [ticket di supporto](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) per ulteriori indagini.

+++

[Torna al passaggio 1](#step-1)

Fai clic [QUI](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/site-down-troubleshooting-diagram) per visualizzare il diagramma di flusso per la risoluzione dei problemi del sito.

## Lettura correlata

[Best practice per la modifica delle tabelle del database](https://experienceleague.adobe.com/it/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) nel playbook di implementazione di Commerce
