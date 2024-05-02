---
title: "Avvisi gestiti per Adobe Commerce: avviso critico del disco"
description: In questo articolo vengono illustrati i passaggi per la risoluzione dei problemi quando si riceve un avviso di disco critico per Adobe Commerce in New Relic. È necessaria un'azione immediata per risolvere il problema. L’avviso avrà un aspetto simile al seguente, a seconda del canale di notifica dell’avviso selezionato.
exl-id: 03e5694b-7689-4fbf-8781-636fa46ca0d3
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: c829b4383fa808df29aab03229c59f06ef8a38bc
workflow-type: tm+mt
source-wordcount: '669'
ht-degree: 0%

---

# Avvisi gestiti per Adobe Commerce: avviso disco critico

In questo articolo vengono illustrati i passaggi per la risoluzione dei problemi quando si riceve un avviso di disco critico per Adobe Commerce in New Relic. È necessaria un&#39;azione immediata per risolvere il problema. L’avviso avrà un aspetto simile al seguente, a seconda del canale di notifica dell’avviso selezionato.

![avviso critico del disco](assets/disk-critical-magento-managed.png){width="500"}

## Prodotti e versioni interessati

Infrastruttura cloud Adobe Commerce su architettura ProPlan

## Problema

Riceverai un avviso in New Relic se ti sei iscritto a [Avvisi gestiti per Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) e una o più soglie di allarme sono state superate. Questi avvisi sono stati sviluppati da Adobe per fornire ai clienti un set standard utilizzando le informazioni provenienti da Supporto e Progettazione.

<u> **Sì!** </u>

* Interrompi qualsiasi distribuzione pianificata fino a quando l&#39;avviso non viene cancellato.
* Attiva immediatamente la modalità di manutenzione se il sito non risponde o se non risponde completamente. Per i passaggi, consulta [Guida all’installazione > Abilitare o disabilitare la modalità di manutenzione](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) . Assicurarsi di aggiungere l&#39;IP all&#39;elenco degli indirizzi IP esenti per assicurarsi di poter accedere al sito per la risoluzione dei problemi. Per i passaggi, consulta [Gestisci l&#39;elenco di indirizzi IP esenti](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt).

**Non farlo!**

* Avvia ulteriori campagne di marketing che possono portare ulteriori visualizzazioni di pagina sul sito.
* Eseguire indicizzatori o nodi aggiuntivi che possono causare ulteriore stress alla CPU o al disco.
* Esegui le principali attività amministrative (ad esempio, amministrazione di Commerce, importazioni/esportazioni di dati).
* Cancella la cache.

Il sito potrebbe non rispondere (se non si è già verificata un’interruzione) se si esegue una delle azioni &quot;Non rispondere&quot; prima di aver indagato e risolto la causa dell’avviso.

## Soluzione

Per identificare e risolvere la causa, seguire la procedura riportata di seguito.

>[!WARNING]
>
>Poiché si tratta di un avviso critico, si consiglia vivamente di completare **Passaggio 1** prima di provare a risolvere il problema (passaggio 2 in poi).

1. Controlla se è presente un ticket di supporto Adobe Commerce. Per i passaggi, consulta [Tracciare i ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) nella nostra knowledge base di supporto. Il supporto potrebbe aver ricevuto un avviso di soglia New Relic, aver creato un ticket e iniziato a lavorare sul problema. Se non esiste alcun ticket, creane uno. Il ticket deve contenere le seguenti informazioni:
   * Motivo contatto: selezionare &quot;Avviso New Relic CRITICAL ricevuto&quot;.
   * Descrizione dell&#39;avviso.
   * [Collegamento per incidente New Relic](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Questo è incluso nel tuo [Avvisi gestiti per Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md).
1. In New Relic, esaminare i dischi per ottenere il massimo utilizzo. Per i passaggi, fai riferimento alla scheda Archiviazione su New Relic [Pagina Host di monitoraggio infrastruttura:](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#storage)
   * Se in New Relic si osserva un lento aumento nell&#39;utilizzo del disco, provare le seguenti opzioni:
   * Ottimizzazione dello spazio su disco regolando l&#39;allocazione dello spazio. Per i passaggi, consulta [Gestisci spazio su disco](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html) nella documentazione per gli sviluppatori. Potresti anche aver bisogno di più spazio su disco (contatta il team dell’account Adobe).
   * Libera spazio su disco per MySQL. Fai riferimento a [Spazio su disco MySQL insufficiente](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md) nella knowledge base di supporto per i passaggi.
   * Se New Relic mostra un utilizzo del disco in rapida crescita, ciò potrebbe indicare che si è verificato un problema che ha causato un aumento molto rapido di un file in una directory. Effettua i seguenti controlli:
1. Controllare lo spazio su disco complessivo per identificare il problema eseguendo il comando seguente in CLI/Terminal: `df -h`
1. Dopo aver identificato una directory con un utilizzo del disco inaspettatamente elevato e crescente, è necessario controllare il file system interessato. L&#39;esempio seguente mostra come controllare la directory dei file `pub/media/`. Directory utilizzata da Commerce per l&#39;archiviazione dei log e dei file multimediali di grandi dimensioni. Tuttavia, è necessario eseguire questo comando per qualsiasi directory che mostri un utilizzo imprevisto del disco: `du -sch ~/pub/media/*`

Se l&#39;output del terminale mostra un file in una di queste directory che aumenta rapidamente nell&#39;utilizzo del disco e si sa che il contenuto del file non è necessario, si consiglia di rimuovere il file. Se non si sente a suo agio nell’eseguire questa azione, [invia un ticket di supporto Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
