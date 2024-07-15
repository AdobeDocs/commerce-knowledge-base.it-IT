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

Questo articolo fornisce soluzioni per i casi in cui lo spazio su MySQL in Adobe Commerce su infrastrutture cloud è molto ridotto o assente. I sintomi possono includere interruzioni del sito, impossibilità per i clienti di aggiungere prodotti al carrello, impossibilità di connettersi al database, accesso al database in remoto e impossibilità di SSH nel nodo. I sintomi includono anche Galera, sincronizzazione dell’ambiente, PHP, database ed errori di distribuzione come elencato di seguito. Fai clic su [Soluzione](https://support.magento.com/hc/en-us/articles/360058472572#solution) per passare direttamente alla sezione della soluzione.

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

* *php: PDO::\_\_costrutto(): il server MySQL non è più disponibile.*
* *errori php: PDO::\_\_costrutto(): errore durante la lettura del pacchetto di saluto. PID=NNNN.*
* *ERRORE 2013 (HY000): connessione al server MySQL interrotta durante la lettura del pacchetto di comunicazione iniziale. Errore di sistema: 0 &quot;Errore interno/verifica (non errore di sistema)&quot;.*

Errori database:

* *Errore\_code: 1114*
* *InnoDB: errore (spazio su disco insufficiente) durante la scrittura del nodo di Word nella tabella indice ausiliaria FTS.*
* *SQLSTATE\[HY000\]: errore generale: il server MySQL 2006 non è più disponibile*
* *\[ERROR\] SQL secondario: Errore &#39;La tabella `<table\_name>` è piena&#39; nella query.*
* *L&#39;unità mysql.service ha immesso lo stato non riuscito.*
* *errore: &#39;Impossibile connettersi al server MySQL locale tramite il socket &#39;/var/run/mysqld/mysqld.sock&#39; (111 &quot;Connessione rifiutata&quot;)&#39;*
* *1205 Timeout attesa blocco superato. Provare a riavviare la transazione. Query: INSERT INTO \`cron\_schedule\` (\`job\_code\`, \`status\`, \`created\_at\`, \`scheduled\_at\`) VALORI (?, ?, `YYYY-02-07 HH:MM:SS`, `YYYY-MM-DD HH:MM:SS`)*

Errori di distribuzione:

* *E: il comando &#39;\[&#39;sudo&#39;, &#39;-u&#39;, `<environment name>`, &#39;bash&#39;, &#39;-c&#39;, &#39;/etc/platform/`<environment name>`/post\_deploy.sh&#39;\]&#39; ha restituito uno stato di uscita diverso da zero 255*
* *E: il comando &#39;\[&#39;ssh&#39;, u`<node IP address>`, &#39;sudo /usr/bin/sv -w 30 restart site-`<environment name>`g-nginx&#39;\]&#39; ha restituito un valore diverso da zero*
* *Aggiornamento dello schema.. SQLSTATE\[HY000\]: Errore generale: 1114 Tabella `<table\_name>` piena*
* *SQLSTATE\[HY000\]: errore generale: 3 Errore durante la scrittura del file ./`<environment name>`/\#*
* *W: `<filename>` (codice di errore: 28 &quot;Spazio esaurito nel dispositivo&quot;)* *Errori di indicizzazione (insieme a file .ibd temporanei orfani in /tmp):*
* *L&#39;indicizzatore della regola catalogo genera un&#39;eccezione. Le tabelle temporanee non vengono pulite in seguito e quindi riempiono il disco nel nodo master MySQL corrente*

<u>Passaggi da riprodurre</u>:

Uno dei modi per verificare se `/data/mysql` (o dove è configurato l&#39;archivio dati MySQL) è pieno consiste nell&#39;eseguire il comando seguente in CLI:

```bash
df -h
```

Meno del 10% della memoria disponibile sul disco MySQL è un indicatore primario di un&#39;interruzione.

## Causa

Il mount `/data/mysql` potrebbe diventare pieno a causa di una serie di problemi, ad esempio la mancanza di un numero sufficiente di nodi, di spazio di archiviazione disponibile e di query non valide che generano tabelle temporanee.

## Soluzione

Esiste un passo immediato che è possibile compiere per riportare MySQL sulla strada giusta (o impedire che si blocchi): liberare spazio scaricando le tabelle di grandi dimensioni.

Una soluzione a lungo termine, tuttavia, consiste nell&#39;allocare più spazio e seguire le [best practice per il database](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html), inclusa l&#39;abilitazione della funzionalità [Archivio ordini/fatture/spedizioni](https://docs.magento.com/user-guide/sales/order-archive.html).

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

### Cerca file `ibtmp1` di grandi dimensioni

Verificare la presenza di un file `ibtmp1` di grandi dimensioni su `/data/mysql` di ciascun nodo: questo file è la tablespace per le tabelle temporanee. Le eventuali query non valide che generano tabelle temporanee sono contenute nel file `ibtmp1`. Questo file viene rimosso solo al riavvio del database. Se il database occupa tutto lo spazio disponibile, è necessario riavviarlo. Se sono presenti query non valide, verranno ricreate di nuovo.

### Svuota tabelle di grandi dimensioni

>[!WARNING]
>
>Si consiglia vivamente di creare un backup del database prima di eseguire eventuali manipolazioni ed evitarle durante i periodi di caricamento elevato del sito. Vedi [Scarica il database](https://devdocs.magento.com/cloud/project/project-webint-snap.html#db-dump) nella documentazione per gli sviluppatori.

Controlla se ci sono tabelle di grandi dimensioni e considera se una di esse può essere scaricata. Esegui questa operazione sul nodo principale (sorgente).

Ad esempio, le tabelle con i rapporti possono in genere essere scaricate. Per informazioni dettagliate su come trovare tabelle di grandi dimensioni, vedere l&#39;articolo [Trova tabelle MySQL grandi](/help/how-to/general/find-large-mysql-tables.md).

Se non sono presenti tabelle di report di grandi dimensioni, è consigliabile svuotare `_index` tabelle per rimettere in sesto l&#39;applicazione Adobe Commerce. `index_price` tabelle sono le più idonee. Ad esempio, `catalog_category_product_index_storeX` tabelle, dove X può avere valori da &quot;1&quot; al numero massimo di archivi. Tieni presente che dovrai reindicizzare per ripristinare i dati in queste tabelle e, nel caso di cataloghi di grandi dimensioni, questa reindicizzazione potrebbe richiedere molto tempo.

Una volta scaricati, attendere il completamento della sincronizzazione wsrep. È ora possibile creare backup e adottare misure più significative per aggiungere più spazio, ad esempio allocando/acquistando più spazio e abilitando la funzionalità [Archivio ordini/fatture/spedizioni](https://docs.magento.com/user-guide/sales/order-archive.html).

### Verifica impostazioni di registrazione binaria

Verificare le impostazioni di registrazione binaria del server MySQL: `log_bin` e `log_bin_index`. Se le impostazioni sono attivate, i file di registro potrebbero diventare enormi. [Crea un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) richiedendo di eliminare file di registro binari di grandi dimensioni. Inoltre, verifica che la registrazione binaria sia configurata correttamente in modo che i registri vengano eliminati periodicamente e non richiedano troppo spazio.

Se non si dispone dell&#39;accesso alle impostazioni del server MySQL, richiedere il supporto per la verifica.

### Alloca/acquista più spazio

Allocare più spazio su disco per MySQL se si dispone di alcuni elementi inutilizzati. Consulta l&#39;articolo [Verifica il limite di spazio su disco](/help/how-to/general/check-disk-space-limit-for-magento-commerce-cloud.md) per informazioni su come verificare se è disponibile spazio su disco.

* Per la combinazione Starter, tutti gli ambienti e gli ambienti Pro plan Integration, è possibile allocare lo spazio su disco se ne sono inutilizzati alcuni. Per ulteriori dettagli, vedere [Allocare più spazio per MySQL](/help/how-to/general/allocate-more-space-for-mysql-in-magento-commerce-cloud.md).
* Per gli ambienti di produzione e staging del piano Pro, [contatta il supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) per allocare più spazio su disco se ne sono inutilizzati alcuni.

Se hai raggiunto il limite di spazio e riscontri ancora problemi di spazio insufficiente, puoi acquistare altro spazio su disco. Per ulteriori informazioni, contatta il team dell’account di Adobe.
