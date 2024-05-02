---
title: "Avvisi gestiti su Adobe Commerce: avviso critico memoria Redis"
description: Questo articolo descrive i passaggi per la risoluzione dei problemi relativi a quando ricevi un avviso critico di memoria Redis per Adobe Commerce in New Relic. Per risolvere il problema è necessaria un'azione immediata. L’avviso avrà un aspetto simile al seguente, a seconda del canale di notifica dell’avviso selezionato.
exl-id: 28e1d879-d7ca-4439-8e81-52a1fbf3ecb0
feature: Cache, Categories, Observability, Services, Support, Tools and External Services, Variables
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '690'
ht-degree: 0%

---

# Avvisi gestiti su Adobe Commerce: Avvisi critici per la memoria Redis

Questo articolo descrive i passaggi per la risoluzione dei problemi relativi a quando ricevi un avviso critico di memoria Redis per Adobe Commerce in New Relic. Per risolvere il problema è necessaria un&#39;azione immediata. L’avviso avrà un aspetto simile al seguente, a seconda del canale di notifica dell’avviso selezionato.

![new_relic_redis_memory_critical.png](assets/new_relic_redis_memory_critical.png)

## Prodotti e versioni interessati

Tutte le versioni di Adobe Commerce su infrastruttura cloud Architettura del piano Pro

## Problema

Riceverai un avviso in New Relic se ti sei iscritto a [Avvisi gestiti per Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) e una o più soglie di allarme sono state superate. Questi avvisi sono stati sviluppati da Adobe per fornire ai commercianti un set standard di avvisi utilizzando le informazioni provenienti da Supporto e Progettazione.

**<u>Sì!</u>**

* Interrompi qualsiasi distribuzione pianificata fino a quando l&#39;avviso non viene cancellato.
* Attiva immediatamente la modalità di manutenzione se il sito non risponde o se non risponde completamente. Per i passaggi, consulta [Guida all’installazione > Abilitare o disabilitare la modalità di manutenzione](/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html#enable-or-disable-maintenance-mode-1) nella nostra Guida all’installazione. Assicurarsi di aggiungere l&#39;IP all&#39;elenco degli indirizzi IP esenti per assicurarsi di poter accedere al sito per la risoluzione dei problemi. Per i passaggi, consulta [Gestisci l&#39;elenco di indirizzi IP esenti](/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html#maintain-the-list-of-exempt-ip-addresses) nella nostra Guida all’installazione.

**<u>Non farlo!</u>**

* Avvia ulteriori campagne di marketing che possono portare ulteriori visualizzazioni di pagina sul sito.
* Eseguire indicizzatori o nodi aggiuntivi che possono causare ulteriore stress alla CPU o al disco.
* Esegui le principali attività amministrative (ad esempio, azioni principali nell’amministratore di Commerce come importazioni/esportazioni di dati, scaricamento dei supporti, salvataggio delle categorie con un numero elevato di prodotti assegnati e aggiornamenti di massa).
* Cancella la cache.

## Soluzione

Per identificare e risolvere la causa, seguire la procedura riportata di seguito.

**Poiché si tratta di un avviso critico, si consiglia vivamente di completare il passaggio 1 prima di provare a risolvere il problema (dal passaggio 2 in poi).**

1. Controlla se è presente un ticket di supporto Adobe Commerce. Per i passaggi, consulta [Tracciare i ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) nella nostra knowledge base di supporto. Il supporto potrebbe aver già ricevuto un avviso di soglia New Relic, creato un ticket e iniziato a lavorare sul problema. Se non esiste alcun ticket, creane uno. Il ticket deve contenere le seguenti informazioni:

   * Motivo contatto: selezionare &quot;Avviso New Relic CRITICAL ricevuto&quot;.
   * Descrizione dell&#39;avviso.
   * [Collegamento al problema New Relic](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents/). Questo è incluso nel tuo [Avvisi gestiti per Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md).

1. Se non esiste alcun ticket di supporto, verificare se la memoria Redis utilizzata è in aumento o in diminuzione andando su [one.newrelic.com](https://login.newrelic.com) > **Infrastruttura** > **Servizi di terze parti** , selezionare il dashboard Redis. Se è stabile o in aumento, [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) per eseguire l&#39;upsize del cluster o aumentare il `maxmemory` limita al livello successivo.
1. Se non riesci a identificare la causa dell’aumento del consumo di memoria Redis, controlla le tendenze recenti per identificare i problemi relativi alle recenti distribuzioni del codice o alle modifiche alla configurazione (ad esempio, nuovi gruppi di clienti e modifiche di grandi dimensioni al catalogo). È consigliabile verificare negli ultimi sette giorni di attività le correlazioni presenti nelle distribuzioni o nelle modifiche del codice.
1. Verifica se le estensioni di terze parti non si comportano correttamente:

   * Prova a trovare una correlazione con le estensioni di terze parti installate di recente e l’ora di inizio del problema.
   * Esamina le estensioni che potrebbero potenzialmente influenzare la cache di Adobe Commerce e causarne la rapida crescita. Ad esempio, blocchi di layout personalizzati, sostituzione della funzionalità della cache e memorizzazione di grandi quantità di dati nella cache.

1. Se non vi sono prove di malfunzionamento delle estensioni, [Installare le ultime patch per risolvere i problemi Redis per Adobe Commerce sull’infrastruttura cloud](/help/troubleshooting/miscellaneous/install-latest-patches-to-fix-magento-redis-issues.md).
1. Se i passaggi precedenti non ti aiutano a identificare o risolvere il problema, puoi abilitare la cache L2 per ridurre il traffico di rete tra l’app e Redis. Per informazioni generali sulla cache L2, fare riferimento a [Memorizzazione nella cache L2 nell’applicazione Adobe Commerce](/docs/commerce-operations/configuration-guide/cache/level-two-cache.html) nella documentazione per gli sviluppatori. Per abilitare la cache L2 per l’infrastruttura cloud, prova quanto segue:

   * Aggiornare la versione ECE Tools se precedente alla versione 2002.1.2.
   * Configurare la cache L2 utilizzando [Usa variabile REDIS\_BACKEND](/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) e aggiornamento `.magento.env.yaml` file:

   ```yaml
   stage:
       deploy:
           REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
   ```
