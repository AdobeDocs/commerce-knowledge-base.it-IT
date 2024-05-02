---
title: Spazio su disco MySQL insufficiente in Adobe Commerce sull’infrastruttura cloud
description: Questo articolo fornisce soluzioni per i casi in cui lo spazio su MySQL in Adobe Commerce su infrastrutture cloud è molto ridotto o assente. I sintomi possono includere interruzioni del sito, impossibilità per i clienti di aggiungere prodotti al carrello, impossibilità di connettersi al database, accesso al database in remoto e impossibilità di SSH nel nodo. I sintomi includono anche Galera, sincronizzazione dell’ambiente, PHP, database ed errori di distribuzione come elencato di seguito. Fare clic su [Soluzione](https://support.magento.com/hc/en-us/articles/360058472572#solution) per passare direttamente alla sezione della soluzione.
exl-id: 788c709e-59f5-4062-ab25-5ce6508f29f9
feature: Catalog Management, Categories, Cloud, Paas, Services
role: Developer
source-git-commit: 667fcacd5b6cbf56a5fd919d0683ad6a0f979fca
workflow-type: tm+mt
source-wordcount: '1157'
ht-degree: 0%

---

# Spazio su disco MySQL insufficiente in Adobe Commerce sull’infrastruttura cloud

Questo articolo fornisce soluzioni per i casi in cui lo spazio su MySQL in Adobe Commerce su infrastrutture cloud è molto ridotto o assente. I sintomi possono includere interruzioni del sito, impossibilità per i clienti di aggiungere prodotti al carrello, impossibilità di connettersi al database, accesso al database in remoto e impossibilità di SSH nel nodo. I sintomi includono anche Galera, sincronizzazione dell’ambiente, PHP, database ed errori di distribuzione come elencato di seguito. Clic [Soluzione](https://support.magento.com/hc/en-us/articles/360058472572#solution) per passare direttamente alla sezione della soluzione.

## Prodotti e versioni interessati

Adobe Commerce sull’infrastruttura cloud 2.3.0-2.3.6-p1, 2.4.0-2.4.2

## Problema

Il database diventa troppo grande. I sintomi possono includere perdita della connessione al database, errore di caricamento del database e una serie di altri problemi.

Errori che potresti riscontrare:

Galera:

* *SQLSTATE\[08S01\]: errore collegamento di comunicazione: WSREP 1047 non ha ancora preparato il nodo per l&#39;utilizzo dell&#39;applicazione*   *Errori di importazione:*
* *SQLSTATE\[HY000\]: Errore generale: 1180 Errore ricevuto 5 &quot;Errore di input/output&quot;*
* *SQLSTATE\[08S01\]: errore collegamento di comunicazione: WSREP 1047 non ha ancora preparato il nodo per l&#39;utilizzo dell&#39;applicazione*

Errori di sincronizzazione ambiente:

* *SQLSTATE: errore generale: 1180 Errore 5 &quot;Errore di input/output&quot; durante COMMIT*

Errori PHP:

* *php: PDO::\_\_costrutto(): il server MySQL è scomparso.*
* *errori php: PDO::\_\_costrutto(): errore durante la lettura del pacchetto di saluto. PID=NNNN.*
* *ERRORE 2013 (HY000): connessione al server MySQL interrotta durante la lettura del pacchetto di comunicazione iniziale. Errore di sistema: 0 &quot;Errore interno/verifica (non errore di sistema)&quot;.*

Errori database:

* *Errore\_code: 1114*
* *InnoDB: errore (spazio su disco insufficiente) durante la scrittura del nodo di Word nella tabella dell&#39;indice ausiliario FTS.*
* *SQLSTATE\[HY000\]: errore generale: il server MySQL 2006 non è più disponibile*
* *\[ERROR\] SQL secondario: Errore &#39;Tabella `<table\_name>` è pieno&#39; su query.*
* *L&#39;unità mysql.service è entrata in stato di errore.*
* *errore: &#39;Impossibile connettersi al server MySQL locale tramite il socket &#39;/var/run/mysqld/mysqld.sock&#39; (111 &quot;Connessione rifiutata&quot;)&#39;*
* *1205 Timeout attesa blocco superato. Provare a riavviare la transazione. Query: INSERT INTO \`cron\_schedule\` (\`job\_code\`, \`status\`, \`created\_at\`, \`scheduled\_at\`) VALORI (?, ?, `YYYY-02-07 HH:MM:SS`, `YYYY-MM-DD HH:MM:SS`)*

Errori di distribuzione:

* *E: Comando &#39;\[&#39;sudo&#39;, &#39;-u&#39;, `<environment name>`, &#39;bash&#39;, &#39;-c&#39;, &#39;/etc/platform/`<environment name>`/post\_deploy.sh&#39;\]&#39; ha restituito lo stato di uscita 255 diverso da zero*
* *E: Comando &#39;\[&#39;ssh&#39;, u`<node IP address>`, &#39;sudo /usr/bin/sv -w 30 riavvia sito-`<environment name>`g-nginx&#39;\]&#39; ha restituito un valore diverso da zero*
* *Aggiornamento dello schema.. SQLSTATE\[HY000\]: Errore generale: 1114 Tabella `<table\_name>` è pieno*
* *SQLSTATE\[HY000\]: errore generale: 3 Errore durante la scrittura del file ./`<environment name>`/\#*
* *L: `<filename>` (Codice di errore: 28 &quot;Spazio esaurito sul dispositivo&quot;)*  *Errori di indicizzazione (insieme a file temporanei .ibd orfani in /tmp):*
* *L’indicizzatore della regola catalogo genera un’eccezione. Le tabelle temporanee non vengono pulite in seguito e quindi riempiono il disco nel nodo master MySQL corrente*

<u>Passaggi da riprodurre</u>:

Uno dei modi per verificare se `/data/mysql` (o quando l&#39;archiviazione dati MySQL è configurata) è pieno eseguendo il seguente comando nella CLI:

```bash
df -h
```

Meno del 10% della memoria disponibile sul disco MySQL è un indicatore primario di un&#39;interruzione.

## Causa

Il `/data/mysql` il mount potrebbe diventare completo a causa di una serie di problemi, ad esempio la mancanza di un numero sufficiente di nodi, di spazio di archiviazione disponibile e di query non valide che generano tabelle temporanee.

## Soluzione

Esiste un passo immediato che è possibile compiere per riportare MySQL sulla strada giusta (o impedire che si blocchi): liberare spazio scaricando le tabelle di grandi dimensioni.

Ma una soluzione a lungo termine potrebbe essere quella di allocare più spazio e seguire [Best practice per il database](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html), compresa l&#39;attivazione [Archivio ordini/fatture/spedizioni](https://docs.magento.com/user-guide/sales/order-archive.html) funzionalità.

Di seguito sono riportati dettagli sulle soluzioni rapide e a lungo termine.

### Controllare e liberare gli interni

Assicurati che siano disponibili abbastanza nodi. A tale scopo, eseguire il comando seguente:

```bash
df -i
```

L’output sarà simile al seguente:

```bash
Filesystem Inodes   Used   Free Use% Mounted on
/dev/nvme2n1 655360    1695  653665    1% /data/mysql
```

Verificare che % d&#39;uso sia &lt;70%. Gli nodi sono correlati con i file. Se si rimuovono file dalla partizione, si libereranno gli inodi.

### Controllare e liberare spazio di archiviazione

Controllare lo spazio di archiviazione disponibile. A questo scopo, esegui:

```bash
df -k
```

L’output sarà simile al seguente:

```bash
Size Used Avail Use% Mounted on·
       50G 49G 95M 100% /data/mysql
```

Se % d&#39;uso è > 70%, è necessario intervenire per liberare/aggiungere spazio.

### Controlla le dimensioni grandi `ibtmp1` file

Controlla le dimensioni grandi `ibtmp1` file su `/data/mysql` di ciascun nodo: questo file è la tablespace per le tabelle temporanee. Se sono presenti query non valide che generano tabelle temporanee, queste sono contenute in `ibtmp1` file. Questo file viene rimosso solo al riavvio del database. Se il database occupa tutto lo spazio disponibile, è necessario riavviarlo. Se sono presenti query non valide, verranno ricreate di nuovo.

### Svuota tabelle di grandi dimensioni

>[!WARNING]
>
>Si consiglia vivamente di creare un backup del database prima di eseguire eventuali manipolazioni ed evitarle durante i periodi di caricamento elevato del sito. Consulta [Eseguire il dump del database](https://devdocs.magento.com/cloud/project/project-webint-snap.html#db-dump) nella documentazione per gli sviluppatori.

Controlla se ci sono tabelle di grandi dimensioni e considera se una di esse può essere scaricata. Esegui questa operazione sul nodo principale (sorgente).

Ad esempio, le tabelle con i rapporti possono in genere essere scaricate. Per informazioni dettagliate su come trovare tabelle di grandi dimensioni, vedere [Trova tabelle MySQL di grandi dimensioni](/help/how-to/general/find-large-mysql-tables.md) articolo.

Se non sono presenti tabelle di rapporti di grandi dimensioni, è consigliabile eseguire lo scaricamento `_index` per rimettere in sesto l’applicazione Adobe Commerce. `index_price` Le tabelle sarebbero i candidati migliori. Ad esempio: `catalog_category_product_index_storeX` tabelle, dove X può avere valori compresi tra &quot;1&quot; e il numero massimo di archivi. Tieni presente che dovrai reindicizzare per ripristinare i dati in queste tabelle e, nel caso di cataloghi di grandi dimensioni, questa reindicizzazione potrebbe richiedere molto tempo.

Una volta scaricati, attendere il completamento della sincronizzazione wsrep. È ora possibile creare backup e adottare misure più significative per aggiungere più spazio, ad esempio allocare/acquistare più spazio e abilitare [Archivio ordini/fatture/spedizioni](https://docs.magento.com/user-guide/sales/order-archive.html) funzionalità.

### Verifica impostazioni di registrazione binaria

Verificare le impostazioni di registrazione binaria di MySQL Server: `log_bin` e `log_bin_index`. Se le impostazioni sono attivate, i file di registro potrebbero diventare enormi. [Creare un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) richiesta di eliminazione di file di registro binari di grandi dimensioni. Inoltre, verifica che la registrazione binaria sia configurata correttamente in modo che i registri vengano eliminati periodicamente e non richiedano troppo spazio.

Se non si dispone dell&#39;accesso alle impostazioni del server MySQL, richiedere il supporto per la verifica.

### Alloca/acquista più spazio

Allocare più spazio su disco per MySQL se si dispone di alcuni elementi inutilizzati. Consulta la [Verifica limite di spazio su disco](/help/how-to/general/check-disk-space-limit-for-magento-commerce-cloud.md) articolo per informazioni su come verificare se è disponibile spazio su disco.

* Per la combinazione Starter, tutti gli ambienti e gli ambienti Pro plan Integration, è possibile allocare lo spazio su disco se ne sono inutilizzati alcuni. Per ulteriori informazioni, vedere [Alloca più spazio per MySQL](/help/how-to/general/allocate-more-space-for-mysql-in-magento-commerce-cloud.md).
* Per ambienti Pro plan di staging e produzione, [contatta l’assistenza](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) per allocare più spazio su disco se ne sono inutilizzati alcuni.

Se hai raggiunto il limite di spazio e riscontri ancora problemi di spazio insufficiente, puoi acquistare altro spazio su disco. Per ulteriori informazioni, contatta il team dell’account di Adobe.
