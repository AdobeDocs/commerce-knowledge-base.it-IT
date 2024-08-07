---
title: Come richiedere l’upsize temporaneo dell’infrastruttura cloud per Adobe Commerce
description: Se la tua organizzazione sta pianificando un evento online in cui si prevede un traffico elevato, o se improvvisamente scopri che il tuo sito sta attraversando un evento con traffico elevato, puoi inviare un [Ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) per richiedere una capacità cloud temporanea aggiuntiva per il tuo Adobe Commerce sull’archivio dell’infrastruttura cloud.
exl-id: 561e2bdd-718a-45c1-8b6c-a0e3a6c8ad04
feature: Cloud, Iaas
source-git-commit: 357e0acb1c849079ff0fe9f53fe386f60475c7f9
workflow-type: tm+mt
source-wordcount: '898'
ht-degree: 0%

---

# Come richiedere l’upsize temporaneo dell’infrastruttura cloud per Adobe Commerce

Se la tua organizzazione sta pianificando un evento online in cui si prevede un traffico elevato, o se improvvisamente scopri che il tuo sito sta subendo un evento con traffico elevato, puoi inviare un [ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) per richiedere una capacità cloud temporanea aggiuntiva per il tuo Adobe Commerce sull&#39;archivio dell&#39;infrastruttura cloud.

>[!NOTE]
>
>È necessario un preavviso di 48 ore lavorative per le richieste di upsize non di emergenza. Gli aggiornamenti per le campagne promozionali non sono considerati emergenze a meno che il sito non sia completamente non funzionante o riceva un traffico molto più elevato del previsto e le prestazioni siano state gravemente ridotte.

## Prodotti e versioni interessati

* Adobe Commerce sull&#39;infrastruttura cloud, tutte le [versioni supportate](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## Come identificare gli eventi di traffico elevato

In New Relic Alerts, puoi utilizzare le condizioni di avviso di base per definire soglie che si adattano al comportamento dei tuoi dati.

Gli avvisi della linea di base sono utili per creare condizioni di avviso che:

* Invia una notifica solo quando i dati si comportano in modo anomalo.
* Adeguamento dinamico ai dati e alle tendenze in continua evoluzione, comprese le tendenze giornaliere o settimanali.

Inoltre, gli avvisi della linea di base funzionano bene con le nuove applicazioni quando non si hanno ancora comportamenti noti.

Segui questo collegamento per ulteriori informazioni sul rilevamento delle anomalie in New Relic [con Intelliegence applicato](https://docs.newrelic.com/docs/alerts-applied-intelligence/applied-intelligence/anomaly-detection/anomaly-detection-applied-intelligence/).

Se ricevi una notifica di avviso che suggerisce un evento con traffico elevato, potrebbe essere necessario prendere in considerazione l&#39;invio di [un ticket di supporto](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket) per richiedere una capacità aggiuntiva. Segui i passaggi seguenti.

## Come monitorare le prestazioni del sito

Adobe fornisce una serie di criteri di avviso New Relic per Adobe Commerce sull’infrastruttura cloud Architettura del piano Pro e Adobe Commerce sull’infrastruttura cloud Architettura del piano Starter Ambienti di produzione per monitorare le seguenti metriche delle prestazioni chiave:

* [Punteggio Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction)
* Percentuale di errori
* Spazio su disco (disponibile solo negli ambienti di produzione con architettura Pro)

In base alle best practice del settore, queste regole impostano le soglie per le avvertenze e le condizioni critiche che influiscono sulle prestazioni. Quando il sito presenta un problema di infrastruttura o applicazione che attiva una soglia di avviso, New Relic invia notifiche di avviso in modo da poter affrontare il problema in modo proattivo. Per utilizzare questi criteri, è necessario configurare i canali di notifica per la ricezione dei messaggi di avviso.

Segui questo collegamento per scoprire come [configurare avvisi basati sulle prestazioni](/docs/commerce-cloud-service/user-guide/monitor/new-relic.html#monitor-performance-with-managed-alerts).

## Passaggi per richiedere un upsize temporaneo

Segui i passaggi seguenti per inviare un [ticket di supporto](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket) per richiedere una capacità cloud temporanea aggiuntiva:

Invia un [ticket di supporto al Centro assistenza Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) dopo aver immesso le seguenti informazioni:

>[!NOTE]
>
>L&#39;opzione *Richiesta di aumento festività* è disponibile solo tra i mesi di ottobre e dicembre.

1. Selezionare il prodotto Adobe Commerce per il quale si desidera ricevere supporto.
1. Completare i primi quattro campi (Prodotto, Organizzazione, Tipo di implementazione, Oggetto).
1. Seleziona *Adobe Commerce Cloud Infrastructure* nel menu a discesa **Contact Reason**.
1. Seleziona *Richiesta capacità di aumento festività* nelle opzioni a discesa **Motivo contatto infrastruttura Adobe Commerce**. Fai clic su **OK** nel messaggio a comparsa con richiesta di un preavviso di 48 ore lavorative per richieste temporanee di capacità cloud aggiuntiva.
1. Selezionare le date per i campi obbligatori **Ridimensiona data iniziale** e **Ridimensiona data finale**. Anche l&#39;**Ora inizio ridimensionamento** preferito è un campo obbligatorio.
1. Completare i quattro campi successivi.
1. Nel campo **Descrizione**, se disponi di informazioni aggiuntive sulle dimensioni, forniscile qui. Se non sono richieste dimensioni maggiori specifiche, verrà effettuato un upsize fino alla successiva capacità di dimensioni dell’ambiente più grande. Le richieste di sovraccarico verranno impostate in modo predefinito sulla dimensione successiva maggiore rispetto alla dimensione corrente. Se hai bisogno di ulteriore capacità, indicalo nel campo **Descrizione**. La capacità aumentata verrà dedotta dai giorni di sovraccarico o dai giorni vCPU. La finestra di aumento della capacità è solitamente di cinque giorni, ma se hai bisogno di più o meno giorni, indicalo nel [ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

>[!NOTE]
>
>Una volta pianificato l’upsize, un sistema automatizzato regolerà le dimensioni dell’istanza cloud. Al termine della procedura non si riceverà alcuna notifica di ticket. È possibile utilizzare lo strumento Osservazione per Adobe Commerce per visualizzare i tipi di istanza di AWS o Azure per [verificare la modifica](/help/how-to/general/check-vcpu-using-observation-for-adobe-commerce.md).

## Visualizzare la cronologia degli upsize

Puoi visualizzare la cronologia delle dimensioni richieste richiedendo le informazioni al tuo **CSM (Customer Success Manager)**.
Per ogni richiesta di ridimensionamento sono disponibili le seguenti informazioni:

* **Data inizio dimensioni**: data della richiesta di upsize.
* **Data di fine dimensioni**: data in cui il cluster è stato riportato alle dimensioni precedenti.
* **vCPU Size**: dimensione del cluster dopo l&#39;upsize.
* **Utilizzo giorni**: per quanti giorni il cluster è stato sottoposto a upsize.
* **Periodo vCPU**: le dimensioni della vCPU sono state modificate in base al numero di giorni di utilizzo. (ad esempio, la dimensione vCPU 192 x 25 giorni equivale a 4.800).


## Lettura correlata

* Per informazioni approfondite, metodi ed esempi su come misurare e migliorare le prestazioni del sito, consulta i seguenti articoli approfonditi nella knowledge base di supporto:
   * [Calcolo dell’allocazione della CPU per Adobe Commerce su cloud](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-cpu-allocation-calculation.html)
   * [Controlla se l&#39;upsize per le istanze dell&#39;host è necessario per Adobe Commerce sul cloud](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-if-upsize-for-hosts-instances-is-needed.html)
   * [Verifica la configurazione della CPU dell&#39;host per Adobe Commerce sul cloud](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-hosts-cpu-configuration.html)
* Per informazioni su come identificare le interruzioni, consulta [Identificare e misurare le interruzioni per Adobe Commerce sul cloud](/docs/commerce-knowledge-base/kb/how-to/how-to-identify-outages.html) nella knowledge base di supporto.
* Per informazioni sul miglioramento delle prestazioni del sito per evitare la necessità di utilizzare un aumento della capacità, consulta questi articoli nella documentazione per sviluppatori:
   * [Ridimensionamento immagine](/docs/commerce-admin/catalog/products/digital-assets/product-image-config.html#product-image-resizing)
   * [Memorizzazione in cache di pagine intere](/docs/commerce-admin/systems/tools/cache-management.html#full-page-caching)
   * [Utensili ECE](/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/package-overview.html)
