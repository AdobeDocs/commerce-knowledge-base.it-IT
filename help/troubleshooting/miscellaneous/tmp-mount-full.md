---
title: Risolvere i problemi relativi al montaggio /tmp pieno per Adobe Commerce
description: Questo articolo fornisce una soluzione per quando il mount "/tmp" è pieno, il sito potrebbe essere inattivo e non è possibile eseguire SSH in un nodo.
exl-id: e72d0f99-0060-474b-bb1c-2851896e1e43
feature: Storage
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 0%

---

# Risolvere i problemi relativi al montaggio /tmp pieno per Adobe Commerce

Questo articolo fornisce una soluzione per quando il mount `/tmp` è pieno, il sito potrebbe essere inattivo e non è possibile eseguire SSH in un nodo.

## Prodotti e versioni interessati

* Adobe Commerce 2.3.0 - 2.3.6-p1, 2.4.0 - 2.4.2

## Problema

Il montaggio `/tmp` pieno potrebbe causare una serie di possibili sintomi, inclusi i seguenti errori:

* *SQLSTATE[HY000]: errore generale: 3 Errore durante la scrittura del file*
* *Codice errore: 28*
* *Spazio insufficiente sul dispositivo (28)*
* *errore session_start(): non riuscito: non è rimasto spazio sul dispositivo*
* *ERRORE 1 (HY000): impossibile creare/scrivere nel file &#39;/tmp/*
* *Errore SQL: 3, SQLState: HY000*
* *Errore generale: disco 1021 pieno (/tmp)*
* *Impossibile accedere al nodo tramite SSH:*
  *bash: impossibile creare il file temporaneo per here-document: Spazio non disponibile sul dispositivo*
* *errno: 28 &quot;Spazio insufficiente sul dispositivo&quot;*
* *mysqld: il disco sta scrivendo completamente &#39;/tmp&#39;*
* *[ERRORE] mysqld: disco pieno (/tmp)*
* *SQLSTATE[HY000]: errore generale: 1 Impossibile creare/scrivere nel file &#39;/tmp/&#39;*
* *SQLSTATE[HY000]: errore generale: 23 risorse esaurite all&#39;apertura del file &#39;/tmp/&#39;*
* *Codice di errore: 24 &quot;Troppi file aperti&quot;*
* *Errore: 23: risorse esaurite all&#39;apertura del file*


<u>Passaggi da riprodurre:</u>

Per verificare il livello di riempimento del mount `/tmp`, nell&#39;interfaccia CLI passare a `/tmp` ed eseguire il comando seguente:

```bash
 df -h
```

<u>Risultato previsto</u>:

Inferiore all’80%.

<u>Risultato effettivo</u>:

Circa il 100%.

## Causa

Il mount `/tmp` contiene troppi file, che potrebbero essere causati da:

* Query SQL non valide che generano tabelle temporanee di grandi dimensioni e/o troppo grandi.
* Servizi che scrivono nella directory `/tmp`.
* Backup/dump del database rimasti nella directory `/tmp`.

## Soluzione

Per liberare spazio una sola volta, è possibile eseguire alcune operazioni. Sono inoltre disponibili procedure consigliate che impediscono a `\tmp` di raggiungere il pieno.

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

Verificare che Use% sia &lt;70%. Gli nodi sono correlati con i file. Se si rimuovono file dalla partizione, si libereranno gli inodi.

### Controllare e liberare spazio di archiviazione

Alcuni servizi potrebbero salvare i file in `/tmp`.

#### Verifica e libera spazio MySQL

Segui le istruzioni in [Spazio su disco MySQL insufficiente in Adobe Commerce su infrastruttura cloud > Controlla e libera spazio di archiviazione](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md#check_and_free) nella nostra knowledge base di supporto.

#### Controlla le heapdum di Elasticsearch

>[!WARNING]
>
>Le immagini heap contengono informazioni di registrazione che potrebbero essere utili per l’analisi dei problemi. Valuta di conservarli in una posizione separata per almeno 10 giorni.

Rimuovi le heapdump (`*.hprof`) tramite la shell di sistema:

```bash
find /tmp/*.hprof -type f -delete
```

Se non disponi delle autorizzazioni necessarie per eliminare i file creati da un altro utente (in questo caso, ad Elasticsearch), ma noti che i file sono di grandi dimensioni, [crea un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) per gestirli.

#### Controllare le immagini/i backup del database

>[!WARNING]
>
>I backup del database vengono in genere creati per uno scopo specifico. Se non sai se il file è ancora necessario, puoi spostarlo in una posizione diversa invece di eliminarlo.

Controllare `/tmp` per `.sql` o `.sql.gz` file e pulirli. Questi potrebbero essere stati creati da strumenti ece durante il backup o durante la creazione manuale di immagini di database con lo strumento `mysqldump`.

### Best practice

Per evitare problemi con `/tmp` pieno, seguire queste raccomandazioni:

* Non utilizzare MySQL per la ricerca. L&#39;Elasticsearch per la ricerca in genere elimina la necessità della maggior parte delle creazioni di tabelle temporanee pesanti. Consulta [Configurare Adobe Commerce per utilizzare Elasticsearch](https://experienceleague.adobe.com/it/docs/commerce-operations/configuration-guide/search/configure-search-engine) nella documentazione per gli sviluppatori.
* Evitare di eseguire la query `SELECT` su colonne senza indici, in quanto questa operazione occupa una grande quantità di spazio su disco temporaneo. Puoi anche aggiungere gli indici.
* Creare un cron per pulire `/tmp` eseguendo il comando seguente in CLI:

  ```bash
  sudo find /tmp -type f -atime +10 -delete
  ```

## Lettura correlata

[Lo spazio su disco di MySQL nell&#39;infrastruttura cloud di Adobe Commerce](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md) è insufficiente nella Knowledge Base di supporto.
