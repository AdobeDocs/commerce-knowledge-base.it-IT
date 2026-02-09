---
title: Ripristino dello stato precedente dell’ambiente senza snapshot cloud
description: Questo articolo mostra due soluzioni per eseguire il rollback di un ambiente senza avere un’istantanea dell’ambiente su Adobe Commerce sull’infrastruttura cloud.
exl-id: 834d13a7-3b1a-460c-9ed0-9d560105f436
feature: Build, Cloud, Console
source-git-commit: d7c714cf5b2f9db139440d814af26c12001bb4d9
workflow-type: tm+mt
source-wordcount: '784'
ht-degree: 0%

---

# Ripristino dello stato precedente dell’ambiente senza snapshot cloud

Questo articolo mostra due soluzioni per eseguire il rollback di un ambiente senza avere un’istantanea dell’ambiente su Adobe Commerce sull’infrastruttura cloud.

## Prodotti e versioni interessati

* Adobe Commerce sull&#39;infrastruttura cloud, [tutte le versioni supportate](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

Scegliere il caso più appropriato:

* Se si dispone di una build stabile ma non di uno snapshot valido - [Scenario 1: nessuna snapshot, build stabile (connessione SSH disponibile)](#scen2).
* Se la build è interrotta e non si dispone di uno snapshot valido - [Scenario 2: nessuno snapshot; build interrotta (nessuna connessione SSH)](#scen3).

## Scenario 1: nessuna istantanea, compilazione stabile (connessione SSH disponibile) {#scen2}

Questa sezione mostra come eseguire il rollback di un ambiente quando non è stata creata una copia istantanea ma è possibile accedere all’ambiente tramite SSH.

I passaggi sono i seguenti:

1. Disabilita Gestione configurazione.
1. Disinstallare il software Adobe Commerce.
1. Reimposta il ramo Git.

Dopo aver eseguito questi passaggi:

* l&#39;installazione di Adobe Commerce ritorna allo stato Vanilla (database ripristinato; configurazione di distribuzione rimossa; directory in `var` cancellate)
* il ramo git è reimpostato sullo stato desiderato in passato

Leggi i passaggi dettagliati seguenti:

### Passaggio 0 (prerequisito): rimuovere config.php per disabilitare Configuration Management {#disable_config_management}

È necessario disabilitare Gestione configurazione in modo che non applichi automaticamente le impostazioni di configurazione precedenti durante la distribuzione.

Per disabilitare Gestione configurazione, assicurarsi che la directory `/app/etc/` non contenga i file `config.php` (per Adobe Commerce 2.4.x) o `config.local.php` (per Adobe Commerce 2.1.x).

Per rimuovere il file di configurazione, effettuare le seguenti operazioni:

1. [SSH nell&#39;ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Rimuovi il file di configurazione:
   * Per Adobe Commerce 2.4:

   ```php
    rm app/etc/config.php
   ```

   * Per Adobe Commerce 2.1:

   ```php
     rm app/etc/config.local.php
   ```

Per ulteriori informazioni sulla gestione della configurazione, consulta [Gestione della configurazione per le impostazioni dello store](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) nella documentazione per gli sviluppatori.

### Passaggio 1: disinstallare il software Adobe Commerce con il comando setup:uninstall {#setup-uninstall}


La disinstallazione del software Adobe Commerce provoca la perdita e il ripristino del database, la rimozione della configurazione di distribuzione e la cancellazione delle directory in `var`.

Consulta [Disinstallare il software Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall.html) nella documentazione per gli sviluppatori.

Per disinstallare il software Adobe Commerce, effettuare le seguenti operazioni:

1. [SSH nell&#39;ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Esegui `setup:uninstall`:

   ```php
     php bin/magento setup:uninstall
   ```

1. Confermare la disinstallazione.

Per confermare la disinstallazione corretta viene visualizzato il seguente messaggio:

```php
[SUCCESS]: Magento uninstallation complete.
```

Questo significa che abbiamo ripristinato l’installazione di Adobe Commerce (incluso DB) al suo stato autentico (Vanilla).

### Passaggio 2: reimpostare il ramo Git {#reset-git-branch}

Con il ripristino di Git, il codice viene ripristinato allo stato desiderato nel passato.

1. Clona l’ambiente nell’ambiente di sviluppo locale. Puoi copiare il comando nella console Cloud:    ![copia_git_clone.png](assets/copy_git_clone.png)
1. Accedi alla cronologia dei commit. Utilizza `--reverse` per visualizzare la cronologia in ordine inverso per maggiore comodità:

   ```git
     git log --reverse
   ```

1. Seleziona l’hash di commit su cui sei stato bravo. Per ripristinare il codice al suo stato autentico (Vanilla), individua il primo commit che ha creato il ramo (ambiente).    ![Selezione di un hash di commit nella console Git](assets/select_commit_hash.png)
1. Applica ripristino Git rigido:

   ```git
     git reset --h <commit_hash>
   ```

1. Invia modifiche al server:

   ```git
     git push --force <origin> <branch>
   ```

Dopo aver eseguito questi passaggi, il ramo Git viene reimpostato e l’intero registro Git changelog è cancellato. L’ultimo push Git attiva la ridistribuzione per applicare tutte le modifiche e reinstallare Adobe Commerce.

## Scenario 2: nessuna istantanea; compilazione interrotta (nessuna connessione SSH) {#scen3}

In questa sezione viene illustrato come eseguire il rollback di un ambiente quando si trova in uno stato critico: la procedura di distribuzione non riesce a creare un’applicazione funzionante, rendendo così la connessione SSH non disponibile.

In questo scenario, devi innanzitutto ripristinare lo stato di funzionamento dell’applicazione Adobe Commerce utilizzando Git reset, quindi disinstallare il software Adobe Commerce (per eliminare e ripristinare il database, rimuovere la configurazione di distribuzione, ecc.). Lo scenario prevede gli stessi passaggi dello scenario 1, ma l’ordine dei passaggi è diverso ed è presente un ulteriore passaggio: forzare la ridistribuzione. I passaggi sono i seguenti:

[&#x200B;1. Reimposta il ramo Git.](/help/how-to/general/reset-environment-on-cloud.md#reset-git-branch)

[2. Disabilita gestione configurazione.](/help/how-to/general/reset-environment-on-cloud.md#disable_config_management)

[&#x200B;3. Disinstallare il software Adobe Commerce.](/help/how-to/general/reset-environment-on-cloud.md#setup-uninstall)

4&amp;period; Forza ridistribuzione.

Dopo aver eseguito questi passaggi, si otterranno gli stessi risultati dello Scenario 1.

### Passaggio 4: forzare la ridistribuzione

Esegui un commit (potrebbe essere vuoto, anche se non è consigliato) e invialo al server per attivarne la ridistribuzione:

```git
git commit --allow-empty -m "<message>" && git push <origin> <branch>
```

## Se il programma di installazione :uninstall non riesce, reimpostare il database manualmente

Se l&#39;esecuzione del comando `setup:uninstall` ha esito negativo e non può essere completata, è possibile cancellare il database manualmente con la procedura seguente:

1. [SSH nell&#39;ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Connettersi al database MySQL:

   ```sql
   mysql -h database.internal
   ```

1. Rilascia il database `main`:

   ```sql
   drop database main;
   ```

1. Crea un database `main` vuoto:

   ```sql
   create database main;
   ```

1. Eliminare i seguenti file di configurazione: `config.php`, `config.php` `.bak`, `env.php` e `env.php.bak`.

Dopo aver reimpostato il database, [invia un messaggio Git all&#39;ambiente per attivare la ridistribuzione](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html#git-commands) e installa Adobe Commerce in un database appena creato. Oppure [eseguire il comando di ridistribuzione](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html#environment-commands).

## Lettura correlata

Nella documentazione per gli sviluppatori:

* [Ripristinare uno snapshot nel cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#restore-a-manual-backup)
* [Crea uno snapshot](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#create-a-manual-backup)
* [Snapshot e gestione backup](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots)
* [Gestire i rami con Cloud Console - Visualizzare i registri](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/console-branches.html?lang=en#view-logs)
* [Errore di distribuzione del componente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/recover-failed-deployment.html)
* [Gestisci il progetto](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html#configure-the-project)
