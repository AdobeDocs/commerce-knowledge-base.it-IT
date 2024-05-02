---
title: "Avvisi gestiti su Adobe Commerce: avviso di memoria Redis"
description: '"Questo articolo descrive i passaggi per la risoluzione dei problemi relativi a quando ricevi un avviso di Redis per Adobe Commerce in New Relic. Per risolvere il problema è necessaria un''azione immediata. L’avviso avrà un aspetto simile al seguente, a seconda del canale di notifica dell’avviso selezionato:’'
exl-id: b7867a42-3817-4cb4-93cf-d69acee33a41
feature: Categories, Marketing Tools, Observability, Services, Support, Tools and External Services, Variables
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---

# Avvisi gestiti su Adobe Commerce: avviso di memoria Redis

Questo articolo descrive i passaggi per la risoluzione dei problemi relativi a quando ricevi un avviso di Redis per Adobe Commerce in New Relic. Per risolvere il problema è necessaria un&#39;azione immediata. L’avviso avrà un aspetto simile al seguente, a seconda del canale di notifica dell’avviso selezionato:

![new_relic_redis_memory_warning.png](assets/new_relic_redis_memory_warning.png)

## Prodotti e versioni interessati

Tutte le versioni di Adobe Commerce su infrastruttura cloud Architettura del piano Pro.

## Problema

Riceverai un avviso in New Relic se ti sei iscritto a [Avvisi gestiti per Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) e una o più soglie di allarme sono state superate. Questi avvisi sono stati sviluppati da Adobe per fornire ai commercianti un set standard di avvisi utilizzando le informazioni provenienti da Supporto e Progettazione.

**<u>Sì!</u>**

* Si consiglia di interrompere qualsiasi distribuzione pianificata fino alla cancellazione dell&#39;avviso.
* Se il sito non risponde o non risponde più, attiva immediatamente la modalità di manutenzione. Per i passaggi, consulta [Guida all’installazione > Abilitare o disabilitare la modalità di manutenzione](/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html#enable-or-disable-maintenance-mode-1) nella nostra Guida all’installazione.
* Assicurarsi di aggiungere l&#39;IP all&#39;elenco degli indirizzi IP esenti per assicurarsi di poter accedere al sito per la risoluzione dei problemi. Per i passaggi, consulta [Gestisci l&#39;elenco di indirizzi IP esenti](/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html#maintain-the-list-of-exempt-ip-addresses) nella nostra Guida all’installazione.

**<u>Non farlo!</u>**

* Avvia ulteriori campagne di marketing che possono portare ulteriori visualizzazioni di pagina sul sito.
* Eseguire indicizzatori o nodi aggiuntivi che possono causare ulteriore stress alla CPU o al disco.
* Esegui le principali attività amministrative (ad esempio, azioni principali nell’amministratore di Commerce, come importazioni/esportazioni di dati, scaricamento dei file multimediali, salvataggio delle categorie con un numero elevato di prodotti assegnati e aggiornamenti di massa).
* Cancella la cache.

## Soluzione

Per identificare e risolvere la causa, seguire la procedura riportata di seguito.

1. Verificare se la memoria utilizzata Redis è in aumento o in diminuzione andando su [one.newrelic.com](https://login.newrelic.com/login) > **Infrastruttura** > **Servizi di terze parti** , selezionare il dashboard Redis. Se è stabile o in aumento, [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) per eseguire l&#39;upsize del cluster o aumentare il `maxmemory` limita al livello successivo.
1. Se non riesci a identificare la causa dell’aumento del consumo di memoria Redis, controlla le tendenze recenti per identificare i problemi relativi alle recenti distribuzioni del codice o alle modifiche alla configurazione (ad esempio, nuovi gruppi di clienti e modifiche di grandi dimensioni al catalogo). È consigliabile verificare negli ultimi sette giorni di attività le correlazioni presenti nelle distribuzioni o nelle modifiche del codice.
1. Verifica se le estensioni di terze parti non si comportano correttamente:
   * Prova a trovare una correlazione con le estensioni di terze parti installate di recente e l’ora di inizio del problema.
   * Esamina le estensioni che potrebbero potenzialmente influenzare la cache di Adobe Commerce e causarne la rapida crescita. Ad esempio, blocchi di layout personalizzati, sostituzione della funzionalità della cache e memorizzazione di grandi quantità di dati nella cache.
1. Se non vi sono prove di malfunzionamento delle estensioni, [Installare le ultime patch per risolvere i problemi Redis per Adobe Commerce sull’infrastruttura cloud](/help/troubleshooting/miscellaneous/install-latest-patches-to-fix-magento-redis-issues.md). Se i passaggi precedenti non ti aiutano a identificare o risolvere il problema, puoi abilitare la cache L2 per ridurre il traffico di rete tra l’app e Redis. Per informazioni generali sulla cache L2, fare riferimento a [Memorizzazione nella cache L2 nell’applicazione Adobe Commerce](/docs/commerce-operations/configuration-guide/cache/level-two-cache.html) nella nostra Guida alla configurazione. Per abilitare la cache L2 per l’infrastruttura cloud, prova quanto segue:
   * Aggiornare la versione ECE Tools se precedente alla versione 2002.1.2.
   * Configurare la cache L2 utilizzando [Usa variabile REDIS\_BACKEND](/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) e aggiornamento `.magento.env.yaml` file:

   ```yaml
   stage:
      deploy:
          REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
   ```
