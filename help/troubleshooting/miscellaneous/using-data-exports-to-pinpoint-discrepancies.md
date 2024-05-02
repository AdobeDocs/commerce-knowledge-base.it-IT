---
title: Utilizzo delle esportazioni di dati per individuare le discrepanze
description: Questo articolo fornisce soluzioni per la risoluzione dei problemi relativi alle discrepanze nei dati BI di Magento. Le esportazioni di dati sono uno strumento utile per confrontare i dati di Magento BI con i dati di origine al fine di individuare le discrepanze di dati nei rapporti, soprattutto se l'elenco di controllo di [data discrepanza diagnostic checklist](/help/troubleshooting/miscellaneous/diagnosing-a-data-discrepancy.md) non è stato utile per individuare il problema. Questo articolo ti guiderà attraverso un esempio reale di come è possibile individuare le discrepanze di dati utilizzando le esportazioni di dati.
exl-id: b42d585c-ad8c-4685-9ad4-a13686566f18
feature: Commerce Intelligence, Data Import/Export
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '1291'
ht-degree: 0%

---

# Utilizzo delle esportazioni di dati per individuare le discrepanze

Questo articolo fornisce soluzioni per la risoluzione dei problemi relativi alle discrepanze nei dati BI di Magento. Le esportazioni di dati sono uno strumento utile per confrontare i dati di Magento BI con i dati di origine al fine di individuare le discrepanze di dati nei rapporti, soprattutto se [elenco di controllo diagnostico delle discrepanze di dati](/help/troubleshooting/miscellaneous/diagnosing-a-data-discrepancy.md) non ti ha aiutato a individuare il problema. Questo articolo ti guiderà attraverso un esempio reale di come è possibile individuare le discrepanze di dati utilizzando le esportazioni di dati.

Effettua questa analisi, ad esempio:

![](assets/Exports_Discrepancies_1.png)

C&#39;è un calo sospetto a novembre 2014. 500.780,94 dollari di fatturato? Non sembra giusto. Hai confermato che nel database di origine sono visualizzati più ricavi per il mese di novembre 2014 e hai verificato che il **Ricavi** La metrica utilizzata in questo rapporto è definita correttamente. Sembra che i dati nel data warehouse di Magento BI siano incompleti e che sia possibile confermarli utilizzando un’esportazione dati.

## Esportazione dei dati {#export}

Per iniziare, fai clic sull’ingranaggio nell’angolo in alto a destra del grafico, quindi sull’opzione Esportazione non elaborata nel menu a discesa. Questo ti darà un’esportazione non elaborata dei dati dietro il grafico.

![](assets/Export_Discrepancies_5.gif)

Nel menu Esportazione dati non elaborati, potete selezionare la tabella da cui esportare insieme alle colonne da includere nell&#39;esportazione. I filtri possono essere applicati anche al set di risultati.

Nel nostro esempio, il **Ricavi** La metrica utilizzata in questo rapporto utilizza **order\_total** campo definito nel **ordini** tabella, utilizzando **data** come marca temporale. Nella nostra esportazione, vogliamo includere tutti **order\_id** valori per novembre 2014 e relativi **order\_total** . Il **Ricavi** La metrica non utilizza alcun filtro, ma aggiungeremo un filtro all’esportazione per limitare il set di risultati a solo novembre 2014.

Ecco l’aspetto del menu Esportazione dati non elaborati per questo esempio:

![](assets/Exports_Discrepancies_2.png)

Fai clic su Esporta dati per iniziare l’esportazione. Viene visualizzata una finestra con i dettagli dell’esportazione, compreso lo stato. La preparazione dell’esportazione richiede alcuni minuti, il che lo rende un buon momento per eseguire un estratto analogo dei nostri dati sorgente per novembre 2014, tra cui **data, order\_id** e **order\_total** . Il file verrà aperto in Excel e non verrà più aperto, poiché torneremo a utilizzarlo tra breve.

Quando nella finestra Esportazioni dati non elaborati viene visualizzato il pulsante Scarica, fai clic su di esso per scaricare il file zip contenente il file CSV.

![](assets/Export_Discrepancies_6.png)

A questo punto, dobbiamo raccogliere tutti i dati in un unico foglio per trovare il problema. Importeremo il file CSV (l’esportazione da Magento BI) in un foglio diverso del file Excel contenente i nostri dati di origine.

## Individuazione del problema {#pinpoint}

Ora che tutti i dati sono in un unico posto, possiamo cercare la fonte della discrepanza. Confrontare il numero di righe in ogni foglio ci aiuterà a individuare il problema. Esaminiamo più da vicino ogni situazione.

### Entrambi i fogli contengono lo stesso numero di righe

Se entrambi i sistemi hanno lo stesso numero di righe e **Ricavi** metrica non corrisponde ai dati di origine, il valore **order\_total** dev&#39;essere da qualche parte. È possibile che il **order\_total** il campo è stato aggiornato nel database di origine e Magento BI non rileva queste modifiche.

Per confermare, considera se il **order\_total** è in corso una nuova verifica della colonna. Passare al Gestore Date Warehouse e fare clic sulla tabella Ordini. Vedrai il [ricontrolla frequenza](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/analyze/warehouse-manager/cfg-data-rechecks.html) elencati in &quot;Modifiche?&quot; colonna. Il **order\_total** Il campo deve essere impostato in modo da ricontrollare ogni volta che si prevede che cambi; in caso contrario, procedere e impostarlo sulla frequenza di ricontrollo desiderata.

### ![](assets/Export_Discrepancies_4.gif)

Se la frequenza di ricontrollo è già impostata correttamente, c&#39;è un altro problema. Consulta la sezione [Sezione Contattare il supporto tecnico](#support) alla fine di questo articolo per i passaggi successivi.

## Il database di origine contiene PIÙ righe rispetto a Magento BI {#morerows}

Se il database di origine contiene più righe rispetto a Magento BI e lo spazio vuoto è maggiore del numero di ordini che si prevede di immettere durante il ciclo di aggiornamento, potrebbe verificarsi un problema di connessione. Ciò significa che Magento BI non è in grado di estrarre nuovi dati dal database di origine, il che può verificarsi per diversi motivi.

Passare alla pagina Connessioni e controllare lo stato dell&#39;origine dati contenente la tabella dell&#39;ordine:

1. **Se lo stato è Nuova autenticazione** , la connessione non utilizza le credenziali corrette. Fai clic sulla connessione, immetti le credenziali corrette e riprova.
1. **Se lo stato è Non riuscito** , la connessione potrebbe non essere impostata correttamente sul lato server. Le connessioni non riuscite in genere derivano da un nome host errato o dal fatto che il server di destinazione non accetta connessioni sulla porta specificata.Fare clic sulla connessione, controllare l&#39;ortografia del nome host e verificare che la porta corretta sia stata immessa. Sul lato server, verificare che la porta possa accettare connessioni e che il firewall disponga dell&#39;indirizzo IP di Magento BI (54.88.76.97/32) come consentito. **Se la connessione continua a non riuscire** , fare riferimento a [Sezione Contattare il supporto tecnico](#support) alla fine di questo articolo per i passaggi successivi.
1. **Se lo stato è Riuscito** Quindi il problema non è la connessione e il supporto RJ deve essere coinvolto. Consulta la sezione [Sezione Contattare il supporto tecnico](#support) alla fine di questo articolo per i passaggi successivi.

## Il database di origine contiene un numero minore di righe rispetto a Magento BI {#lessrows}

Se il database di origine contiene meno righe rispetto a Magento BI, è possibile che le righe vengano eliminate dal database di origine e che Magento BI non le stia rilevando. ** [Eliminazione dei dati](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/best-practices/data/opt-db-analysis.html) può causare discrepanze, tempi di aggiornamento più lunghi e una serie di problemi logistici** , pertanto ti consigliamo vivamente di non eliminare mai i dati, a meno che non sia realmente necessario.

Se, tuttavia, le righe vengono eliminate dalla tabella, controllare la frequenza di ricontrollo della chiave primaria. Ricontrollare la chiave primaria significa che la tabella verrà controllata per le righe eliminate.

In Gestione Date Warehouse le colonne chiave primaria sono contrassegnate da un simbolo di chiave. Nel nostro esempio, la chiave primaria è **order\_id** colonna:

![](assets/Export_Discrepancies_3.png)

Se la chiave primaria è già impostata per essere ricontrollata o le righe non vengono mai eliminate da questa tabella, sarà necessario il supporto RJ per individuare il problema. Per i passaggi successivi, consulta la sezione seguente.

## Contattare il supporto  {#support}

Se non si è in grado di individuare la fonte del problema, sarà necessario eseguire il ciclo in RJ Support. Prima di inviare un ticket, eseguire le operazioni seguenti:

* **Se il database di origine e Magento BI hanno lo stesso numero di righe** e le frequenze di ricontrollo sono impostate correttamente, esegui una CERCA.VERT nel foglio di calcolo **per individuare i valori order\_id con un diverso valore order\_total tra Magento BI e il database di origine.** Includi questi valori quando invii il ticket.
* **Se il database di origine contiene PIÙ righe rispetto a Magento BI** e la connessione viene visualizzata come Completata o continua a non riuscire, è necessario conoscere il nome della connessione e il messaggio di errore visualizzato, se presente.
* **Se il database di origine contiene un numero INFERIORE di righe rispetto a Magento BI,** le righe non vengono eliminate dalla tabella e le frequenze di ricontrollo sono impostate correttamente. Eseguire una ricerca virtuale nel foglio di calcolo **per trovare i valori order\_id in Magento BI** ma non nel database di origine. Includi questi valori quando invii il ticket.

## Correlato

* [Elenco di controllo diagnostico delle discrepanze di dati](/help/troubleshooting/miscellaneous/diagnosing-a-data-discrepancy.md)
* [Invio di un ticket per discrepanza di dati](https://support.magento.com/hc/en-us/articles/360016506472-Submitting-a-data-discrepancy-ticket)
