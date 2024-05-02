---
title: Risolvere i problemi relativi al montaggio /tmp pieno per Adobe Commerce
description: Questo articolo fornisce una soluzione per quando il mount "/tmp" è pieno, il sito potrebbe essere inattivo e non è possibile eseguire SSH in un nodo.
exl-id: e72d0f99-0060-474b-bb1c-2851896e1e43
feature: Storage
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 0%

---

# Risolvere i problemi relativi al montaggio /tmp pieno per Adobe Commerce

Questo articolo fornisce una soluzione per quando `/tmp` Il mount è pieno, il sito potrebbe essere inattivo e non è possibile eseguire SSH in un nodo.

## Prodotti e versioni interessati

* Adobe Commerce 2.3.0 - 2.3.6-p1, 2.4.0 - 2.4.2

## Problema

Il `/tmp` il montaggio pieno potrebbe causare una serie di possibili sintomi, inclusi i seguenti errori:

* *SQLSTATE[HY000]: errore generale: 3 errore durante la scrittura del file*
* *Codice errore: 28*
* *Spazio insufficiente sul dispositivo (28)*
* *errore session_start(): failed: non è rimasto spazio sul dispositivo*
* *ERRORE 1 (HY000): impossibile creare/scrivere nel file &#39;/tmp/*
* *Errore SQL: 3, stato SQL: HY000*
* *Errore generale: disco 1021 pieno (/tmp)*
* *Impossibile accedere al nodo tramite SSH:*
  *bash: impossibile creare un file temporaneo per here-document: non è rimasto spazio sul dispositivo*
* *errno: 28 &quot;Spazio insufficiente sul dispositivo&quot;*
* *mysqld: il disco sta scrivendo completamente &#39;/tmp&#39;*
* *[ERRORE] mysqld: Disco pieno (/tmp)*
* *SQLSTATE[HY000]: errore generale: 1 impossibile creare/scrivere nel file &#39;/tmp/&#39;*
* *SQLSTATE[HY000]: errore generale: 23 risorse esaurite all’apertura del file &#39;/tmp/&#39;*
* *Codice di errore: 24 &quot;Troppi file aperti&quot;*
* *Errore ricevuto: 23: risorse esaurite all&#39;apertura del file*


<u>Passaggi da riprodurre:</u>

Per verificare il livello di riempimento `/tmp` mount è, nello switch CLI a `/tmp` ed esegui il comando seguente:

```bash
 df -h
```

<u>Risultato previsto</u>:

Inferiore all’80%.

<u>Risultato effettivo</u>:

Circa il 100%.

## Causa

Il `/tmp` Il montaggio contiene troppi file, che potrebbero essere causati da:

* Query SQL non valide che generano tabelle temporanee di grandi dimensioni e/o troppo grandi.
* Servizi che scrivono in `/tmp` directory.
* Backup/dump del database rimasti nel `/tmp` directory.

## Soluzione

Per liberare spazio una sola volta, è possibile eseguire alcune operazioni e sono disponibili best practice che impediscono `\tmp` dal pieno.

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

Esistono diversi servizi in cui è possibile salvare i file `/tmp`.

#### Verifica e libera spazio MySQL

Segui le istruzioni in [Spazio su disco MySQL insufficiente in Adobe Commerce su infrastruttura cloud > Verifica e libera spazio di archiviazione](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md#check_and_free) nella nostra knowledge base di supporto.

#### Controlla le heapdum di Elasticsearch

>[!WARNING]
>
>Le immagini heap contengono informazioni di registrazione che potrebbero essere utili per l’analisi dei problemi. Valuta di conservarli in una posizione separata per almeno 10 giorni.

Rimuovi le immagini heap (`*.hprof`) utilizzando la shell di sistema:

```bash
find /tmp/*.hprof -type f -delete
```

Se non disponi delle autorizzazioni necessarie per eliminare i file creati da un altro utente (in questo caso, ad Elasticsearch), ma noti che i file sono di grandi dimensioni, [creare un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) per occuparsene.

#### Controllare le immagini/i backup del database

>[!WARNING]
>
>I backup del database vengono in genere creati per uno scopo specifico. Se non sai se il file è ancora necessario, puoi spostarlo in una posizione diversa invece di eliminarlo.

Verifica `/tmp` per `.sql` o `.sql.gz` e pulirli. Potrebbero essere state create da strumenti ece durante il backup o durante la creazione manuale di immagini di database utilizzando `mysqldump` strumento.

### Best practice

Per evitare problemi con `/tmp` per essere complete, segui queste raccomandazioni:

* Non utilizzare MySQL per la ricerca. L&#39;Elasticsearch per la ricerca in genere elimina la necessità della maggior parte delle creazioni di tabelle temporanee pesanti. Consulta [Configurare Adobe Commerce per l’utilizzo di Elasticsearch](https://devdocs.magento.com/guides/v2.2/config-guide/elasticsearch/configure-magento.html) nella documentazione per gli sviluppatori.
* Evita di eseguire `SELECT` eseguire query su colonne senza indici, poiché in questo modo viene utilizzata una grande quantità di spazio su disco temporaneo. Puoi anche aggiungere gli indici.
* Creare un cron per la pulizia `/tmp` eseguendo il comando seguente nella CLI:

  ```bash
  sudo find /tmp -type f -atime +10 -delete
  ```

## Lettura correlata

[Spazio su disco MySQL insufficiente in Adobe Commerce sull’infrastruttura cloud](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md) nella nostra knowledge base di supporto.
