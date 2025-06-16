---
title: Risoluzione dei problemi di Reporting avanzato per Adobe Commerce
description: I problemi di Reporting avanzato su Adobe Commerce possono essere risolti utilizzando questo strumento di risoluzione dei problemi. Ciò include il Reporting avanzato, in cui non vengono visualizzati dati ed errori 404. Fare clic su ogni domanda per visualizzare la risposta in ogni passaggio della risoluzione dei problemi.
exl-id: 7ef9870c-b6b6-4144-a5a7-81aa20a1606c
feature: Cache, Support
role: Developer
source-git-commit: 842c329b5d8bacf72ac689412fde5a5d76d16e85
workflow-type: tm+mt
source-wordcount: '1018'
ht-degree: 0%

---

# Risoluzione dei problemi di Reporting avanzato per Adobe Commerce

I problemi di Reporting avanzato su Adobe Commerce possono essere risolti utilizzando questo strumento di risoluzione dei problemi. Ciò include il Reporting avanzato, in cui non vengono visualizzati dati ed errori 404. Fare clic su ogni domanda per visualizzare la risposta in ogni passaggio della risoluzione dei problemi.

## Passaggio 1 - Conferma della conformità del sito ai requisiti di reporting avanzati {#step-1}

+++**Il tuo sito Web soddisfa i requisiti di reporting avanzati?**

Quando si utilizza la funzione di reporting avanzato, viene visualizzata la pagina di errore 404. Il tuo sito Web soddisfa i [requisiti di reporting avanzati](https://experienceleague.adobe.com/it/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#requirements)?

a. SÌ - Procedere al [passaggio 2](#step-2).\
b. NO - Completa i requisiti di reporting avanzato per il tuo sito seguendo i passaggi descritti in [Requisiti di reporting avanzati](https://experienceleague.adobe.com/it/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#requirements). Quindi, procedere al [passaggio 2](#step-2).

+++

## Passaggio 2 - Esistono ordini in più valute di base? {#step-2}

+++**Sono utilizzate più valute di base?**

Vengono utilizzate più valute di base (negli ordini e nella configurazione)? Eseguire il comando [!DNL SQL] per ottenere la configurazione corrente: `SELECT value FROM core_config_data WHERE path = 'currency/options/base';`.

a. SÌ: se la query restituisce più righe, non è possibile utilizzare la funzione di reporting avanzato, in quanto è supportata una sola valuta.\
b. NO - Il risultato mostra una sola valuta. Esempio: `USD`. Sono state utilizzate più valute di base (negli ordini)? Esegui questo comando [!DNL SQL] per ottenere i dati degli ordini cronologici:\
`SELECT DISTINCT base_currency_code FROM sales_order;`.
**NOTA: questo comando richiede un&#39;analisi completa della tabella. Per le tabelle con un numero elevato di record, ciò potrebbe avere un impatto sulle prestazioni durante l&#39;esecuzione della query** per ottenere i dati cronologici degli ordini.
Se sono state utilizzate più valute di base, non è possibile utilizzare la funzione di reporting avanzato, in quanto è supportata una sola valuta. Se nell&#39;output viene visualizzata una sola valuta, passare al [passaggio 3](#step-3).

+++

## Passaggio 3: verificare se il database diviso è in uso {#step-3}

+++**Si sta utilizzando una soluzione di database diviso?**

Stai utilizzando [soluzione di database divisa](https://experienceleague.adobe.com/it/docs/commerce-operations/configuration-guide/storage/split-db/multi-master)?

a. SÌ - Utilizzare la patch **MDVA-26831** nell&#39;errore Advanced Reporting 404 nella soluzione di database diviso e cancellare la cache. Attendere 24 ore per la riesecuzione del processo e riprovare.\
b. NO - Procedi al [passaggio 4](#step-4).

+++

## Passaggio 4: conferma della generazione di rapporti avanzata abilitata {#step-4}

+++**La generazione di rapporti avanzata è abilitata?**

Controlla **Amministratore** > **Archivi** > **Impostazioni** > **Configurazione** > **Generale** > **Generazione avanzata dei rapporti**. Per i passaggi dettagliati, controlla [Reporting avanzato: abilita reporting avanzato](https://experienceleague.adobe.com/it/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#step-1-enable-advanced-reporting).

a. SÌ - Procedere al [passaggio 5](#step-5).\
b. NO - [Abilita la generazione di rapporti avanzati](https://experienceleague.adobe.com/it/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#step-1-enable-advanced-reporting) e salva e attendi 24 ore la sincronizzazione di Adobe Commerce e Advanced Reporting. Verifica se i dati ora vengono caricati. Se è così, hai risolto il problema. Se non si procede al [passaggio 5](#step-5).

+++

## Passaggio 5: verificare la presenza di token {#step-5}

+++**È presente un token?**

Verificare che sia presente un token eseguendo la seguente query: `SELECT * FROM core_config_data WHERE path LIKE 'analytics/general/token' \G` È presente un token?

a. SÌ - Procedere al [passaggio 7](#step-7).\
b. NO - Se il valore del token è NULL o non è presente alcun record nel database, passare al [passaggio 6](#step-6).

+++

## Passaggio 6: utilizzare la riga {#step-6}

+++**La query restituisce la riga?**

Controllare il valore del contatore nella tabella dei flag eseguendo questa query: ``SELECT * FROM `flag` where `flag_code` = 'analytics_link_subscription_update_reverse_counter'\G`` La query restituisce la riga?

a. SÌ - Procedere come segue: 1. Esegui la query seguente:\
``DELETE from `flag` where `flag_code` = 'analytics_link_subscription_update_reverse_counter';``\
2\. [Disattivare e abilitare il modulo di reportistica avanzata](https://experienceleague.adobe.com/it/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#step-1-enable-advanced-reporting) nelle impostazioni e [autorizzare nuovamente il token](https://experienceleague.adobe.com/it/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#verify-that-the-integration-is-active).\
3\. Attendi 24 ore per la sincronizzazione di Adobe Commerce e Advanced Reporting. Se non riesci ancora a visualizzare i dati in Reporting avanzato, [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO - Se la query non restituisce alcun risultato, effettuare le seguenti operazioni: 1. [Disattivare e abilitare il modulo di reportistica avanzata](https://experienceleague.adobe.com/it/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#step-1-enable-advanced-reporting) nelle impostazioni e [autorizzare nuovamente il token](https://experienceleague.adobe.com/it/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#verify-that-the-integration-is-active).\
2\. Attendi 24 ore per la sincronizzazione di Adobe Commerce e Advanced Reporting. Se non riesci ancora a visualizzare i dati in Reporting avanzato, [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Passaggio 7: verifica la presenza di record nella tabella `cron_schedule` {#step-7}

+++**Sono presenti record nella tabella `cron_schedule`?**

Verificare che il processo `analytics_collect_data` sia stato eseguito eseguendo questa query: `SELECT * FROM cron_schedule WHERE job_code LIKE 'analytics_collect_data' \G`

a. SÌ - Se sono presenti record e la colonna **status** riporta _missing_, utilizzare la patch in questo articolo KB Aggiorna report avanzati per eseguire il proprio gruppo cron.\
b. SÌ - Se sono presenti record e la colonna **status** riporta _success_, passare al [passaggio 9](#step-9).\
c. YES - Se sono presenti record e la colonna **status** riporta _error_, passare al [passaggio 8.](#step-8)\
d. NO - Se non sono presenti record, passare al [passaggio 8](#step-8).

+++

## Passaggio 8: verifica la presenza del processo in `support_report.log` {#step-8}

+++**Il processo è stato registrato in `support_report.log`?**

Esegui il comando: `zgrep analytics_collect_data var/log/support_report.log var/log/support_report.log.1.gz | tail`

a. SÌ - Se l&#39;output della query indica un processo riuscito, ad esempio `Cron Job analytics_collect_data is successfully finished` passare al [passaggio 9](#step-9).\
b. NO - Se nel registro non sono presenti record, [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
c. YES - Se sono presenti record ma si è verificato un errore, passare al [passaggio 10](#step-10).

+++

## Passaggio 9: verifica la presenza del file `data.tgz` {#step-9}

+++**Il file `data.tgz` esiste nel sistema e sono presenti record nei registri di accesso?**

Per verificare che il file `data.tgz` esista, eseguire questo comando. Deve restituire le directory con i nomi hash:

```
ls -ltr pub/media/analytics/
```

Per verificare la presenza di record in access.logs, eseguire il comando seguente:

* Su Commerce Cloud:

  ```
  {{zgrep -i analytics /var/log/platform/*/access.log* | grep MagentoBI}}
  ```

* Per On-Premise, sostituisci di conseguenza il percorso del file:
  `zgrep -i analytics <your web server's log path>/access.log* | grep MagentoBI`

a. SÌ - Se il file `data.tgz` è presente e sono presenti record nei registri di accesso, ma si è ancora verificato un errore 404, è necessario [inviare un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO - Procedi al [passaggio 10](#step-10).

+++

## Passaggio 10 - Controllare il messaggio di errore {#step-10}

+++**Il processo cron genera un messaggio di errore?**

Esempio: nella tabella `cron_schedule` viene visualizzato l&#39;errore *Impossibile eliminare il file &quot;/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0*. Avviso!unlink(/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0?lang=en): file o directory non esistente*

a. SÌ - Usa la patch ACSD-50165 in [Impossibile eliminare il file. Avviso!unlink: errore di file o directory non presente dall&#39;amministratore](https://experienceleague.adobe.com/it/docs/experience-cloud-kcs/kbarticles/ka-26887). Attendere 24 ore per la riesecuzione del processo, quindi riprovare.\
b. NO - Procedi al [passaggio 11](#step-11).

+++

## Passaggio 11 - Verificare la presenza di un errore di Page Builder {#step-11}

+++**Si è verificato un errore causato da Page Builder?**

Esempio: `report.ERROR: Cron Job analytics_collect_data has an error: substr_count() expects parameter 1 to be string, null given. Statistics: {"sum":0,"count":1,"realmem":0,"emalloc":0,"realmem_start":224919552,"emalloc_start":216398384} [] []`

a. SÌ - Utilizzare la patch MDVA-19391 in Errori comuni del job cron di Advanced Reporting su Adobe Commerce, attendere 24 ore per l&#39;esecuzione del job e riprovare.\
b. NO - [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

[Torna al passaggio 1](#step-1)

## Lettura correlata

[Best practice per la modifica delle tabelle del database](https://experienceleague.adobe.com/it/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) nel playbook di implementazione di Commerce
