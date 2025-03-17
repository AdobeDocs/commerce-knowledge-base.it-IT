---
title: 'La distribuzione non riesce e viene visualizzato il messaggio "Errore durante la creazione del progetto: hook di compilazione non riuscito con codice di stato 1"'
description: 'Questo articolo illustra le cause e le soluzioni del problema di infrastruttura cloud di Adobe Commerce, in cui la fase di build del processo di distribuzione non riesce e il messaggio di errore è riassunto con: *"Errore durante la creazione del progetto: hook di build non riuscito con codice di stato 1"*.'
exl-id: add1cdac-dbcb-4c55-8bc2-c1f27e24aadb
feature: Build, Deploy
role: Developer
source-git-commit: 6a880a57c6cafb34fa51706f7bab1e23310bcef7
workflow-type: tm+mt
source-wordcount: '745'
ht-degree: 0%

---

# La distribuzione non riesce e viene visualizzato il messaggio &quot;Errore durante la creazione del progetto: hook di compilazione non riuscito con codice di stato 1&quot;

In questo articolo vengono illustrate le cause e le soluzioni del problema relativo all&#39;infrastruttura cloud di Adobe Commerce, in cui la fase di compilazione del processo di distribuzione non riesce e il messaggio di errore viene riepilogato con: *&quot;Errore durante la compilazione del progetto: hook di compilazione non riuscito con codice di stato 1&quot;*.

## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud, tutte le versioni

## Problema

<u>Passaggi da riprodurre</u>:

Attiva la distribuzione manualmente o eseguendo un’unione, un push o una sincronizzazione dell’ambiente.

<u>Risultato previsto</u>:

Distribuzione completata correttamente.

<u>Risultato effettivo</u>:

1. La fase di costruzione non riesce e l’intero processo di distribuzione si blocca.
1. Nel log degli errori di distribuzione, il messaggio di errore termina con: *&quot;Errore durante la compilazione del progetto: hook di compilazione non riuscito con codice di stato 1. Build interrotta&quot;.*

## Causa

Ci sono diversi motivi per cui la creazione dell’ambiente non riesce. In genere, nel registro di distribuzione viene visualizzato un lungo messaggio di errore, in cui la prima parte è più specifica per il motivo e la conclusione è *&quot;Errore durante la creazione del progetto: hook di compilazione non riuscito con codice di stato 1. Build interrotta&quot;.*

Osservando più da vicino la prima parte specifica del problema sarà utile identificare il problema. Di seguito sono elencate le più comuni e la sezione successiva fornisce le relative soluzioni:

* Spazio di archiviazione non disponibile.
* Configurazione ECE-Tools errata.
* La patch che stai tentando di applicare non è compatibile con la versione di Adobe Commerce in uso o presenta conflitti con altre patch applicate o con le tue personalizzazioni.
* Problemi con il codice dei moduli personalizzati impediscono la corretta generazione.

## Soluzione

* Verifica che lo spazio di archiviazione sia sufficiente. Per informazioni su come verificare lo spazio disponibile, vedere l&#39;articolo [Controllare lo spazio su disco nell&#39;ambiente cloud utilizzando CLI](/help/how-to/general/check-disk-space-on-cloud-environment-using-cli.md). È possibile pulire le directory di registro e/o aumentare lo spazio su disco.
* Assicurati che gli strumenti ECE siano configurati correttamente.
* Controllare se il problema è causato dalla patch. Risolvere il conflitto o contattare il [Supporto Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket). Per ulteriori informazioni, consulta di seguito.
* Verifica se è l’estensione personalizzata a causare il problema. Risolvi il conflitto o contatta gli sviluppatori di estensioni per la soluzione.

I paragrafi seguenti forniscono ulteriori dettagli.

### Pulire i registri e/o aumentare lo spazio disponibile

Directory da considerare per la pulizia:

* `var/log`
* `var/report`
* `var/debug/`
* `var`

Per informazioni dettagliate su come aumentare lo spazio su disco se si utilizza l&#39;architettura del piano Starter per l&#39;infrastruttura cloud di Adobe Commerce, vedere [Aumentare lo spazio su disco per l&#39;ambiente di integrazione nel cloud](/help/how-to/general/increase-disk-space-for-integration-environment-on-cloud.md). Le stesse istruzioni possono essere utilizzate per aumentare lo spazio di Adobe Commerce sull’infrastruttura cloud Ambiente di integrazione dell’architettura Pro plan. Per Pro Production/Staging, è necessario inviare un ticket a [Supporto Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) e richiedere maggiore spazio su disco. Ma è monitorato da Platform. In genere, tuttavia, non è necessario occuparsi di questo problema nell’architettura di staging/produzione di Pro, in quanto Adobe Commerce monitora questi parametri per conto dell’utente e avvisa l’utente e/o esegue azioni in base al contratto.

### Verificare che gli strumenti ECE siano configurati correttamente

1. Verificare che gli hook di compilazione siano definiti correttamente nel file `magento.app.yaml`. Se utilizzi Adobe Commerce 2.2.X, gli hook di creazione devono essere definiti come segue:

   ```yaml
   # We run build hooks before your application has been packaged.
   build: |
       php ./vendor/bin/ece-tools build
   # We run deploy hook after your application has been deployed and started.
   deploy: |
       php ./vendor/bin/ece-tools deploy
   ```

   Utilizza l&#39;articolo [Aggiorna a strumenti ece](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/install-package) come riferimento.

1. Verificare che il pacchetto ECE-tools sia presente nel file `composer.lock` eseguendo il comando seguente:

   ```bash
   grep '"name": "magento/ece-tools"' composer.lock
   ```

   Se sono specificati, la risposta sarà simile al seguente esempio:

   ```bash
   "name": "magento/ece-tools", "version": "2002.0.20",
   ```

Consulta l&#39;articolo [Aggiornamento a strumenti ece](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/install-package) per maggiori informazioni.

### È la patch a causare il problema?

Se è la patch applicata a impedire la corretta generazione dell’ambiente, nel registro di distribuzione verrà visualizzato qualcosa di simile al seguente:

```bash
%patch_name%.composer.patch
[2019-02-19 18:12:59] CRITICAL:
....
[2019-02-19 18:12:59] CRITICAL: Command git apply --check --reverse /app/m2-hotfixes/%patch_name%.composer.patch returned code 1
...
W:
W: Command git apply --check --reverse /app/m2-hotfixes/%patch_name%.composer.patch returned code 1
W:
W:
W: build
...
E: Error building project: The build hook failed with status code 1. Aborted build.
```

Questi messaggi di errore indicano che la patch che stai tentando di applicare è stata creata per una versione di Adobe Commerce diversa o è in conflitto con le personalizzazioni o con le patch applicate in precedenza. Prova a risolvere il conflitto o contatta il [supporto Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### È l&#39;estensione la causa del problema?

Se è l’estensione personalizzata a impedire la corretta generazione dell’ambiente, nel registro di distribuzione verranno visualizzati i nomi dei moduli personalizzati e il conflitto specifico causato da questo modulo. Risolvi il conflitto o contatta gli sviluppatori di estensioni per la soluzione.

### Assicurati che le modifiche siano applicate

Eseguire il commit e inviare le modifiche. La distribuzione verrà attivata automaticamente.
