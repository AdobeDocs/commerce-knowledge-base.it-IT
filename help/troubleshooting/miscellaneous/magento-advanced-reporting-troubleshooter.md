---
title: Risoluzione dei problemi di Reporting avanzato per Adobe Commerce
description: I problemi di Reporting avanzato su Adobe Commerce possono essere risolti utilizzando questo strumento di risoluzione dei problemi. Ciò include il Reporting avanzato, in cui non vengono visualizzati dati ed errori 404. Fare clic su ogni domanda per visualizzare la risposta in ogni passaggio della risoluzione dei problemi.
exl-id: 7ef9870c-b6b6-4144-a5a7-81aa20a1606c
feature: Cache, Support
role: Developer
source-git-commit: 84b4ca4c4144381f0b404d2eae6684e7b21755df
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 0%

---

# Risoluzione dei problemi di Reporting avanzato per Adobe Commerce

I problemi di Reporting avanzato su Adobe Commerce possono essere risolti utilizzando questo strumento di risoluzione dei problemi. Ciò include il Reporting avanzato, in cui non vengono visualizzati dati ed errori 404. Fare clic su ogni domanda per visualizzare la risposta in ogni passaggio della risoluzione dei problemi.

## Passaggio 1 - Conferma della conformità del sito ai requisiti di reporting avanzati {#step-1}

+++**Il sito Web soddisfa i requisiti di reporting avanzati?**

Quando si utilizza la funzione di reporting avanzato, viene visualizzata la pagina di errore 404. Il tuo sito web soddisfa [Requisiti di reporting avanzati](https://docs.magento.com/user-guide/reports/advanced-reporting.html#requirements)?

a. SÌ - Procedere come segue [Passaggio 2](#step-2).\
b. NO - Completa i requisiti di Reporting avanzato per il tuo sito seguendo i passaggi descritti in [Requisiti di reporting avanzati](https://docs.magento.com/user-guide/reports/advanced-reporting.html#requirements). Quindi, procedi a [Passaggio 2](#step-2).

+++

## Passaggio 2 - Esistono ordini in più valute di base? {#step-2}

+++**Vengono utilizzate più valute di base?**

Vengono utilizzate più valute di base (negli ordini e nella configurazione)? Esegui questo comando SQL per ottenere la configurazione corrente: `SELECT value FROM core_config_data WHERE path = 'currency/options/base';` .

a. SÌ: se la query restituisce più righe, non è possibile utilizzare la funzione di reporting avanzato, in quanto è supportata una sola valuta.\
b. NO - Il risultato mostra una sola valuta. Esempio: `USD`. Sono state utilizzate più valute di base (negli ordini)? Esegui questo comando SQL per ottenere i dati cronologici degli ordini:\
`SELECT DISTINCT base_currency_code FROM sales_order;`.
**NOTA: questo comando richiede un&#39;analisi completa della tabella, pertanto per le tabelle con un numero elevato di record, potrebbe avere un impatto sulle prestazioni durante l&#39;esecuzione della query** per ottenere i dati cronologici degli ordini.
Se sono state utilizzate più valute di base, non è possibile utilizzare la funzione di reporting avanzato, in quanto è supportata una sola valuta. Se l’output mostra una sola valuta, procedi con [Passaggio 3](#step-3).

+++

## Passaggio 3: verificare se il database diviso è in uso {#step-3}

+++**Si sta utilizzando una soluzione di database diviso?**

Stai utilizzando [soluzione di database suddiviso](https://devdocs.magento.com/guides/v2.3/config-guide/multi-master/multi-master.html)?

a. SÌ - Usare il cerotto **MDVA-26831** in [Errore Advanced Reporting 404 nella soluzione di database suddiviso](/help/troubleshooting/known-issues-patches-attached/advanced-reporting-404-error-on-split-database-solution.md) e cancellare la cache. Attendere 24 ore per la riesecuzione del processo e riprovare.\
b. NO - Procedi a [Passaggio 4](#step-4).

+++

## Passaggio 4: conferma della generazione di rapporti avanzata abilitata {#step-4}

+++**La funzione di reporting avanzato è abilitata?**

Verifica **Amministratore** > **Negozi** > **Impostazioni** > **Configurazione** > **Generale** > **Avanzate**. Per i passaggi dettagliati, rivedi [Reporting avanzato: abilitare il reporting avanzato](https://docs.magento.com/user-guide/reports/advanced-reporting.html#step-1-enable-advanced-reporting).

a. SÌ - Procedere come segue [Passaggio 5](#step-5).\
b. N. - [Abilita reporting avanzato](https://docs.magento.com/user-guide/reports/advanced-reporting.html#step-1-enable-advanced-reporting) e salva e attendi 24 ore per la sincronizzazione di Adobe Commerce e Advanced Reporting. Verifica se i dati ora vengono caricati. Se è così, hai risolto il problema. Se non si procede a [Passaggio 5](#step-5).

+++

## Passaggio 5: verificare la presenza di token {#step-5}

+++**C&#39;è un gettone?**

Verifica la presenza di un token eseguendo la seguente query: `SELECT * FROM core_config_data WHERE path LIKE 'analytics/general/token' \G` C&#39;è un gettone?

a. SÌ - Procedere come segue [Passaggio 7](#step-7).\
b. NO - Se il valore del token è NULL o non è presente alcun record nel database, procedere con [Passaggio 6](#step-6).

+++

## Passaggio 6: utilizzare la riga {#step-6}

+++**La query restituisce la riga?**

Controllare il valore del contatore nella tabella dei flag eseguendo la query seguente: ``SELECT * FROM `flag` where `flag_code` = 'analytics_link_subscription_update_reverse_counter'\G`` La query restituisce la riga?

a. SÌ - Procedere come segue: 1. Esegui la query seguente:\
``DELETE from `flag` where `flag_code` = 'analytics_link_subscription_update_reverse_counter';``\
2\. [Disabilita e abilita il modulo di reporting avanzato](https://docs.magento.com/user-guide/reports/advanced-reporting.html#step-1-enable-advanced-reporting) nelle impostazioni e [autorizza nuovamente il token](https://docs.magento.com/user-guide/reports/advanced-reporting.html#verify-that-the-integration-is-active).\
3\. Attendi 24 ore per la sincronizzazione di Adobe Commerce e Advanced Reporting. Se non riesci ancora a visualizzare i dati in Reporting avanzato, [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO - Se la query non restituisce alcun risultato, effettuare le seguenti operazioni: 1. [Disabilita e abilita il modulo di reporting avanzato](https://docs.magento.com/user-guide/reports/advanced-reporting.html#step-1-enable-advanced-reporting) nelle impostazioni e [autorizza nuovamente il token](https://docs.magento.com/user-guide/reports/advanced-reporting.html#verify-that-the-integration-is-active).\
2\. Attendi 24 ore per la sincronizzazione di Adobe Commerce e Advanced Reporting. Se non riesci ancora a visualizzare i dati in Reporting avanzato, [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Passaggio 7: verificare la presenza di record `cron_schedule` tabella {#step-7}

+++**Ci sono record in `cron_schedule` tavolo?**

Controlla quel processo `analytics_collect_data` è stato eseguito eseguendo questa query: `SELECT * FROM cron_schedule WHERE job_code LIKE 'analytics_collect_data' \G`

a. SÌ - Se sono presenti record e il **stato** la colonna dice _saltato_, utilizza la patch in questo articolo KB [Aggiornare il reporting avanzato in modo che venga eseguito sul proprio gruppo cron](/help/troubleshooting/known-issues-patches-attached/update-advanced-reporting-to-run-on-its-own-cron-group.md).\
b. SÌ - Se sono presenti record e il **stato** la colonna dice _success_, procedi a [Passaggio 9](#step-9).\
c. SÌ - Se sono presenti record e il **stato** la colonna dice _errore_, procedi a [Passaggio 8:](#step-8)\
d. NO - Se non sono presenti record, passare a [Passaggio 8](#step-8).

+++

## Passaggio 8: verificare la presenza di un processo `support_report.log` {#step-8}

+++**Il processo è stato connesso `support_report.log`?**

Esegui il comando: `zgrep analytics_collect_data var/log/support_report.log var/log/support_report.log.1.gz | tail`

a. YES - Se l&#39;output della query indica un job riuscito, ad esempio `Cron Job analytics_collect_data is successfully finished` procedi a [Passaggio 9](#step-9).\
b. NO - Se il registro non contiene alcun dato, [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
c. SÌ - Se sono presenti record ma si è verificato un errore, procedere come segue [Passaggio 10](#step-10).

+++

## Passaggio 9: verifica `data.tgz` file {#step-9}

+++**Il file `data.tgz` sono presenti nel sistema e sono presenti record nei registri di accesso?**

Per verificare che il file `data.tgz` esiste, esegui il comando:

```
ls -ltr pub/media/analytics/<there should be a directory with hash name>/
```

Per verificare la presenza di record in access.logs, eseguire il comando:

```
zgrep -i analytics /var/log/platform/[cluster_id|cluster_id_stg]/access.log* | grep MagentoBI
```

a. SÌ - Se il file `data.tgz` è presente e sono presenti record nei registri di accesso, ma si è ancora verificato un errore 404, è necessario [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO - Procedi a [Passaggio 10](#step-10).

+++

## Passaggio 10 - Controllare il messaggio di errore {#step-10}

+++**Il processo cron genera un messaggio di errore?**

Esempio: nel `core_config_data` tabella in cui viene visualizzato l&#39;errore *Impossibile eliminare il file &quot;/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0*. Avviso!unlink(/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0?lang=en): file o directory non esistente*

a. SÌ - Utilizzare il patch ACSD-50165 in [Impossibile eliminare il file. Attenzione!unlink: errore di file o directory non presente dall&#39;amministratore](/help/troubleshooting/miscellaneous/file-cannot-be-deleated-no-file-or-directory.md), attendere 24 ore per la riesecuzione del processo, quindi riprovare.\
b. NO - Procedi a [Passaggio 11](#step-11).

+++

## Passaggio 11 - Verificare la presenza di un errore di Page Builder {#step-11}

+++**Esiste un errore causato da Page Builder?**

Esempio: `report.ERROR: Cron Job analytics_collect_data has an error: substr_count() expects parameter 1 to be string, null given. Statistics: {"sum":0,"count":1,"realmem":0,"emalloc":0,"realmem_start":224919552,"emalloc_start":216398384} [] []`

a. YES - Utilizzare la patch MDVA-19391 in [Errori comuni del processo cron di Advanced Reporting in Adobe Commerce](/help/troubleshooting/known-issues-patches-attached/advanced-reporting-cron-job-errors-magento-commerce.md), attendi 24 ore per l’esecuzione di nuovo del processo e riprova.\
b. N. - [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

[Torna al passaggio 1](#step-1)
