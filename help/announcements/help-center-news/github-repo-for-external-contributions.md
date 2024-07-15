---
title: La Knowledge Base di supporto Adobe Commerce inizia ad accettare contributi
description: A partire dal 15 giugno, il team della Knowledge Base di supporto Adobe Commerce inizierà ad accettare modifiche dirette e nuovi contributi agli articoli dalla community esterna di Adobe Commerce tramite l’archivio GitHub [magento/knowledge-base](https://github.com/magento/knowledge-base).
exl-id: b5198de0-d6b5-4107-8b74-a12606583596
feature: Support
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---

# La Knowledge Base di supporto Adobe Commerce inizia ad accettare contributi

A partire dal 15 giugno, il team della Knowledge Base di supporto Adobe Commerce inizierà ad accettare modifiche dirette e nuovi contributi agli articoli dalla community esterna di Adobe Commerce tramite l’archivio GitHub [magento/knowledge-base](https://github.com/magento/knowledge-base).

Hai notato un errore di battitura in uno dei nostri articoli o passaggi incompleti per la risoluzione dei problemi?
Ora puoi risolvere il problema autonomamente e ottenere punti di contributo.

## Contribute

Apprezziamo tutti i tipi di contributi, dalle correzioni di errori di battitura minori agli articoli completi per la risoluzione dei problemi. Contribuire a questo archivio ti fa ottenere punti premio, in modo simile a contribuire al codice di Adobe Commerce e alla documentazione per gli sviluppatori. Per ulteriori informazioni, consulta [Contribution reward points](https://github.com/magento/knowledge-base/blob/main/docs/contribution-points.md).

### Flusso contributivo generale

1. Effettua il forking di questo archivio.
1. Apporta modifiche all’archivio con forking.
1. Invia una richiesta di pull (PR) a questo archivio.
1. I test vengono eseguiti:
   * CLA Adobe: accertarsi che il Contratto di licenza per i collaboratori Source aperti di Adobe sia firmato.
   * Test di Markdown Linting: assicurati che la sintassi markdown sia corretta.
   * Test di convalida della struttura del file. Verificare che il commit sia eseguito in base alla [struttura del file richiesta](https://github.com/magento/knowledge-base/blob/main/.github/CONTRIBUTING.md#file_structure).
1. Flusso approvazioni PR:
   1. Gli autori della Knowledge Base di supporto (KB) esaminano il documento PR entro alcuni giorni e aggiungono etichette.
   1. Autore KB può approvare/negare/richiedere modifiche.
   1. Se approvato, KB writer aggiunge etichette corrispondenti al livello di input fornito in PR e Internal Subject matter Expert (SME) rivede la PR.
   1. Lo SME può approvare/negare/richiedere modifiche.
1. Una volta apportate tutte le correzioni (se richieste) e sia l’autore che lo SME della KB approvano la PR, l’autore della KB importa il contenuto nell’archivio interno e lo unisce internamente.
1. L&#39;archivio [magento/knowledge-base](https://github.com/magento/knowledge-base) si sincronizza con quello interno in 20 minuti.
1. Una volta sincronizzati i repository, la PR viene chiusa e si ottengono [punti di contributo](#contribution-points).

Per informazioni dettagliate sul flusso dei contributi, consultare la [Guida per i collaboratori](https://github.com/magento/knowledge-base/blob/main/.github/CONTRIBUTING.md).
Per i modelli, la guida agli stili e le linee guida sulla formattazione, consulta la [documentazione](https://github.com/magento/knowledge-base/tree/main/docs).

### Trovare il file dell’articolo della Knowledge Base di supporto su Github

Nella Knowledge Base di supporto (KB), gli articoli sono organizzati in sezioni, nidificate in categorie.

L&#39;Adobe [Iscrizione agli aggiornamenti dello stato del Magento](/help/how-to/general/how-to-subscribe-to-adobe-magento-status-updates.md) appartiene ad esempio alla sezione Generale della categoria Procedura.

Puoi visualizzare il nome della sezione e della categoria nel percorso delle breadcrumb nella pagina dell’articolo, vedi l’immagine seguente:

![breadcrumb di categorie e sezioni](assets/breadcrumbs.png)

I file articolo sono organizzati nello stesso modo nell&#39;archivio [magento/knowledge-base](https://github.com/magento/knowledge-base).
Tutto il contenuto viene archiviato nella cartella `src`, con cartelle per categorie e cartelle nidificate per sezioni; i nomi dei file coincidono con i titoli degli articoli o sono simili.

Puoi anche utilizzare la ricerca all’interno dell’archivio utilizzando una parte di testo dell’articolo KB di supporto come stringa di ricerca. Quando la ricerca restituisce file che contengono questa stringa, assicurarsi di scegliere il file che appartiene alla sezione e alla categoria corretta.

### Punti contributo

L&#39;archivio [magento/knowledge-base](https://github.com/magento/knowledge-base) è integrato con il team Magento Community Engineering per i punti di contributo e il supporto.

Consulta il documento [Punti contributo](https://github.com/magento/knowledge-base/blob/main/docs/contribution-points.md) per vedere come vengono ricompensati i punti.
