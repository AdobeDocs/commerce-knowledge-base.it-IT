---
title: 'Avvisi gestiti per Adobe Commerce: avviso di disco'
description: Questo articolo fornisce i passaggi per la risoluzione dei problemi quando si riceve un avviso sul disco di avviso per Adobe Commerce in New Relic. È necessaria un'azione immediata per risolvere il problema. L’avviso avrà un aspetto simile al seguente, a seconda del canale di notifica dell’avviso selezionato.
exl-id: 07b34db1-11ec-4cf2-ae47-cfc067f91383
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 0%

---

# Avvisi gestiti per Adobe Commerce: avviso di disco

Questo articolo fornisce i passaggi per la risoluzione dei problemi quando si riceve un avviso sul disco di avviso per Adobe Commerce in New Relic. È necessaria un&#39;azione immediata per risolvere il problema. L’avviso avrà un aspetto simile al seguente, a seconda del canale di notifica dell’avviso selezionato.

![avviso disco](assets/disk-warning-magento-managed.png){width="500"}

## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud, architettura Pro plan.

## Problema

Riceverai un avviso in New Relic se hai firmato fino a [Avvisi gestiti per Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) e una o più soglie di avviso sono state superate. Questi avvisi sono stati sviluppati da Adobe per fornire ai clienti un set standard utilizzando le informazioni provenienti da Supporto e Progettazione.

<u> **Esegui!** </u>

* Interrompi qualsiasi distribuzione pianificata fino a quando l&#39;avviso non viene cancellato.
* Attiva immediatamente la modalità di manutenzione se il sito non risponde o se non risponde completamente. Per i passaggi, fare riferimento alla [Guida all&#39;installazione > Abilitare o disabilitare la modalità di manutenzione](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) nella documentazione per gli sviluppatori. Assicurarsi di aggiungere l&#39;IP all&#39;elenco degli indirizzi IP esenti per assicurarsi di poter accedere al sito per la risoluzione dei problemi. Per ulteriori informazioni, consulta [Gestire l&#39;elenco degli indirizzi IP esenti](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#instgde-cli-maint-exempt) nella documentazione per gli sviluppatori.

<u> **Non fare!** </u>

* Avvia ulteriori campagne di marketing che possono portare ulteriori visualizzazioni di pagina al sito.
* Eseguire indicizzatori o nodi aggiuntivi che possono causare ulteriore stress alla CPU o al disco.
* Esegui le principali attività amministrative (ad esempio, amministrazione di Commerce, importazioni/esportazioni di dati).
* Cancella la cache. Il sito potrebbe non rispondere (se non si è già verificata un’interruzione) se si esegue una delle azioni &quot;Non rispondere&quot; prima di aver indagato e risolto la causa dell’avviso.

## Soluzione

Per identificare la causa e risolverla, procedere come segue:

1. In New Relic, esaminare i dischi per ottenere il massimo utilizzo. Per i passaggi, fare riferimento alla scheda Archiviazione nella pagina Host di monitoraggio dell&#39;infrastruttura [New Relic](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/):
   * Se in New Relic si osserva un lento aumento nell&#39;utilizzo del disco, provare le seguenti opzioni:
   * Ottimizzazione dello spazio su disco regolando l&#39;allocazione dello spazio. Per ulteriori informazioni, consultare [Gestione spazio su disco](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html) nella documentazione per gli sviluppatori. Potresti anche aver bisogno di più spazio su disco (contatta il team dell’account Adobe).
   * Libera spazio su disco per MySQL. Per ulteriori informazioni, consultare [Spazio su disco MySQL insufficiente](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md).
   * Se New Relic mostra un utilizzo del disco in rapida crescita, ciò potrebbe indicare che si è verificato un problema che ha causato un aumento molto rapido di un file in una directory. Effettua i seguenti controlli:
1. Controllare lo spazio su disco complessivo per identificare il problema eseguendo il comando seguente in CLI/Terminal: `df -h`
1. Dopo aver identificato una directory con un utilizzo del disco inaspettatamente elevato e crescente, è necessario controllare il file system interessato. Nell&#39;esempio seguente viene illustrato come controllare la directory dei file `pub/media/`. Questa è la directory che Adobe Commerce utilizza per memorizzare i registri e i file multimediali di grandi dimensioni. Tuttavia, è necessario eseguire questo comando per qualsiasi directory che mostri un utilizzo del disco imprevisto: `du -sch ~/pub/media/*`.

Se l&#39;output del terminale mostra un file in una di queste directory che aumenta rapidamente nell&#39;utilizzo del disco e si sa che il contenuto del file non è necessario, si consiglia di rimuovere il file. Se non hai familiarità con questa azione, [invia un ticket di supporto Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
