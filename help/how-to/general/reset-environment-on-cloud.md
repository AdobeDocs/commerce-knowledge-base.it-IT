---
title: Ripristinare l’ambiente su Adobe Commerce nell’infrastruttura cloud
description: Questo articolo mostra diversi scenari di ripristino dello stato precedente di un ambiente su Adobe Commerce su un’infrastruttura cloud.
exl-id: e6b27838-ca1e-415f-a098-2aa2576e3f20
feature: Best Practices, Build, Cloud, Console
source-git-commit: ddde2385f1d94194b34e9ed51f6cbda55c916d90
workflow-type: tm+mt
source-wordcount: '1087'
ht-degree: 0%

---

# Ripristinare l’ambiente su Adobe Commerce nell’infrastruttura cloud

Questo articolo mostra diversi scenari di ripristino dello stato precedente di un ambiente su Adobe Commerce su un’infrastruttura cloud.

Scegliere il caso più appropriato:

* Se hai pianificato un&#39;attività (implementazione o aggiornamento pianificato): [Scenario 1: attività pianificata](#scen1).
* Se si dispone di un&#39;istantanea valida - [Scenario 2: ripristinare uno snapshot](#scen2).
* Se si dispone di una build stabile, ma non di uno snapshot valido - [Scenario 3: nessuna istantanea, compilazione stabile (connessione SSH disponibile)](#scen3).
* Se la build è interrotta e non si dispone di uno snapshot valido - [Scenario 4: nessuna istantanea; compilazione interrotta (nessuna connessione SSH)](#scen4).

## Scenario 1: attività pianificata

Con un&#39;implementazione o un aggiornamento pianificato, il più semplice e consigliato [!UICONTROL Rollback] sarebbe per il commerciante, come parte dei vostri preparativi, fare quanto segue:

>[!NOTE]
>
>Esegui sempre il test di questi passaggi nel **[!UICONTROL Staging Environment]** prima!

<u>Cinque giorni prima delle attività di aggiornamento/installazione</u>:

1. Controllare le dimensioni del database corrente.
1. Verificare che lo spazio su disco sia sufficiente `/data/exports` per mantenere una [!UICONTROL Database Dump]. Se lo spazio su disco non è sufficiente, rimuovere i dati indesiderati oppure creare un caso di supporto e richiedere l&#39;espansione del disco.

<u>Il giorno delle modifiche</u>:

1. Inserisci il sito web in [!UICONTROL Maintenance Mode].<br>
Ulteriori informazioni su [Attiva o disattiva [!UICONTROL Maintenance Mode]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html) nella guida utente di e [[!UICONTROL Maintenance Mode] opzioni per l&#39;aggiornamento](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/troubleshooting/maintenance-mode-options.html) nella guida all’aggiornamento.
1. Prendi un [[!UICONTROL Database Dump]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/create-database-dump-on-cloud.html).

<u>Se un [!UICONTROL Rollback] è obbligatorio</u>:

1. Se applicazioni come [!DNL MariaDB] è stato aggiornato nell&#39;ambito di questa attività pianificata, fai reinstallare prima l&#39;applicazione a una versione precedente.
1. [!UICONTROL Rollback] il database utilizzando il [!UICONTROL Database Dump]e reimportalo in [!DNL MariaDB].
1. [!UICONTROL Rollback] il codice tramite [!DNL Git] a una versione precedente.

Utilizzo di [!UICONTROL Snapshots] non è il metodo consigliato per l&#39;aggiornamento/attività pianificata [!UICONTROL rollbacks/restores], poiché il recupero dei dati richiede molto più tempo rispetto a un [!UICONTROL Database Dump], come illustrato in precedenza al punto 2 della **Se un [!UICONTROL Rollback] è obbligatorio** sezione.

[!UICONTROL Snapshots] non sono conservati sul nodo/server, sono conservati su un blocco di archiviazione separato e poiché tali dati devono essere trasmessi dall&#39;archiviazione del blocco in rete a un nuovo disco, il processo richiede tempo. Il nuovo disco viene quindi montato sul nodo pronto per il recupero/l&#39;importazione sul disco originale connesso al nodo/server.

Quando si confronta questo con l&#39;importazione di un [!UICONTROL Database Dump], i dati sono già recuperabili sul nodo/server, pertanto viene risparmiato molto tempo in quanto solo [!UICONTROL Database Import] è obbligatorio.

## Scenario 2: ripristinare uno snapshot

Leggi: [Ripristinare un’istantanea su Adobe Commerce nell’infrastruttura cloud](https://devdocs.magento.com/cloud/project/project-webint-snap.html#restore-snapshot) nella documentazione per gli sviluppatori.

>[!NOTE]
>
>La creazione di un’istantanea deve essere il primo passaggio dopo l’accesso all’account Adobe Commerce sull’infrastruttura cloud e prima di applicare modifiche principali. Si tratta di una best practice fortemente consigliata.

Leggi: [Creare un’istantanea](https://devdocs.magento.com/cloud/project/project-webint-snap.html#create-snapshot) nella documentazione per gli sviluppatori.

## Scenario 3: nessuna istantanea, compilazione stabile (connessione SSH disponibile)

Questa sezione mostra come ripristinare un ambiente quando non è stata creata una copia istantanea ma è possibile accedere all’ambiente tramite SSH.

I passaggi sono i seguenti:

1. Disabilita Gestione configurazione.
1. Disinstallare il software Adobe Commerce.
1. Reimposta [!DNL git] filiale.

Dopo aver eseguito questi passaggi:

* L’installazione di Adobe Commerce ritorna allo stato Vanilla (database ripristinato; configurazione di distribuzione rimossa; directory in `var` deselezionato).
* Il tuo [!DNL git] il ramo è stato ripristinato allo stato desiderato in passato.

Leggi i passaggi dettagliati riportati di seguito.

### Passaggio 0 (prerequisito): rimuovere config.php per disabilitare Configuration Management

È necessario disabilitare Gestione configurazione in modo che non applichi automaticamente le impostazioni di configurazione precedenti durante la distribuzione.

Per disabilitare la gestione della configurazione, assicurati che `/app/etc/` la directory non contiene `config.php` file.

Per rimuovere il file di configurazione, effettuare le seguenti operazioni:

1. [SSH per l’ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Rimuovi il file di configurazione: `rm app/etc/config.php`

Ulteriori informazioni sulla gestione della configurazione:

* [Riduzione dei tempi di inattività dell&#39;implementazione su Adobe Commerce su infrastruttura cloud](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md) nella nostra knowledge base di supporto.
* [Gestione della configurazione per le impostazioni dello store](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) nella documentazione per gli sviluppatori.

### Passaggio 1: disinstallare il software Adobe Commerce con il comando setup:uninstall


La disinstallazione del software Adobe Commerce fa cadere e ripristina il database, rimuove la configurazione di distribuzione e cancella le directory in `var`.

Leggi: [Disinstallare il software Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall.html) nella documentazione per gli sviluppatori.

Per disinstallare il software Adobe Commerce, effettuare le seguenti operazioni:

1. [SSH per l’ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Esegui `setup:uninstall` : `bin/magento setup:uninstall`
1. Confermare la disinstallazione.

Per confermare la disinstallazione corretta viene visualizzato il seguente messaggio:

```php
[SUCCESS]: Magento uninstallation complete.
```

Questo significa che abbiamo ripristinato l’installazione di Adobe Commerce (incluso DB) al suo stato autentico (Vanilla).

### Passaggio 2: reimpostare [!DNL git] filiale

Con [!DNL git] ripristinando, il codice torna allo stato desiderato nel passato.

1. Clona l’ambiente nell’ambiente di sviluppo locale. Puoi copiare il comando nella console Cloud:    ![copy_git_clone.png](assets/copy_git_clone.png)
1. Accedi alla cronologia dei commit. Utilizzare `--reverse` per visualizzare la cronologia in ordine inverso per maggiore comodità: `git log --reverse`
1. Seleziona l’hash di commit su cui sei stato bravo. Per ripristinare il codice al suo stato autentico (Vanilla), individua il primo commit che ha creato il ramo (ambiente).
   ![Selezione di un hash di commit nella console Git](assets/select_commit_hash.png)
1. Applicare duramente [!DNL git] ripristina: `git reset --h <commit_hash>`
1. Invia modifiche al server: `git push --force <origin> <branch>`

Dopo aver eseguito questi passaggi, [!DNL git] il ramo viene reimpostato e l&#39;intero [!DNL git] changelog è chiaro. L&#39;ultimo [!DNL git] push attiva la ridistribuzione per applicare tutte le modifiche e reinstallare Adobe Commerce.

## Scenario 4: nessuna istantanea; compilazione interrotta (no [!DNL SSH] connessione)

Questa sezione mostra come ripristinare un ambiente quando si trova in uno stato critico: la procedura di distribuzione non può riuscire a creare un’applicazione funzionante, rendendo così [!DNL SSH] connessione non disponibile.

In questo scenario, devi prima ripristinare lo stato di funzionamento dell’applicazione Adobe Commerce utilizzando [!DNL git] ripristina, quindi disinstalla il software Adobe Commerce (per eliminare e ripristinare il database, rimuovere la configurazione di distribuzione, ecc.). Lo scenario prevede gli stessi passaggi dello scenario 3, ma l’ordine dei passaggi è diverso ed è presente un ulteriore passaggio: forzare la ridistribuzione. I passaggi sono i seguenti:

1. [Reimposta [!DNL git] filiale.](/help/how-to/general/reset-environment-on-cloud.md#reset-git-branch)
1. [Disabilita Gestione configurazione.](/help/how-to/general/reset-environment-on-cloud.md#disable_config_management)
1. [Disinstallare il software Adobe Commerce.](/help/how-to/general/reset-environment-on-cloud.md#setup-uninstall)
1. Forza la ridistribuzione.

Dopo aver eseguito questi passaggi, si otterranno gli stessi risultati dello Scenario 3.

### Passaggio 4: forzare la ridistribuzione

Esegui un commit (potrebbe essere vuoto, anche se non è consigliato) e invialo al server per attivarne la ridistribuzione:

```git
git commit --allow-empty -m "<message>" && git push <origin> <branch>
```

## Se l&#39;installazione:disinstallazione non riesce, reimpostare il database manualmente

Se si esegue `setup:uninstall` Il comando ha esito negativo e non può essere completato. È possibile che il DB venga cancellato manualmente con i seguenti passaggi:

1. [SSH per l’ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Connettersi al database MySQL: `mysql -h database.internal` (Per gli ambienti Pro consulta: [Configura servizio MySQL](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/mysql.html)).
1. Rilasciare il database \`main\`: `drop database main;`
1. Crea un database \`main\` vuoto: `create database main;`
1. Elimina i seguenti file di configurazione: `config.php` , `config.php` , `.bak,` , `env.php`, `env.php.bak`

Dopo aver ripristinato il DB, [creare un [!DNL git] invia all’ambiente per attivare la ridistribuzione](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/examples/example-using-cli.html) e installare Adobe Commerce in un database appena creato. Oppure [eseguire il comando ridistribuisci](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html#environment-commands).
