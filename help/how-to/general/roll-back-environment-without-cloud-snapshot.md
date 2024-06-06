---
title: Ripristino dello stato precedente dell’ambiente senza snapshot cloud
description: Questo articolo mostra due soluzioni per eseguire il rollback di un ambiente senza avere un’istantanea dell’ambiente su Adobe Commerce sull’infrastruttura cloud.
exl-id: 834d13a7-3b1a-460c-9ed0-9d560105f436
feature: Build, Cloud, Console
source-git-commit: 5347e8714ef1374440f5d246100a0221e4b189fc
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 0%

---

# Ripristino dello stato precedente dell’ambiente senza snapshot cloud

Questo articolo mostra due soluzioni per eseguire il rollback di un ambiente senza avere un’istantanea dell’ambiente su Adobe Commerce sull’infrastruttura cloud.

## Prodotti e versioni interessati

* Adobe Commerce sull’infrastruttura cloud, [tutte le versioni supportate](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

Scegliere il caso più appropriato:

* Se si dispone di una build stabile, ma non di uno snapshot valido - [Scenario 1: nessuna istantanea, compilazione stabile (connessione SSH disponibile)](#scen2).
* Se la build è interrotta e non si dispone di uno snapshot valido - [Scenario 2: nessuna istantanea; compilazione interrotta (nessuna connessione SSH)](#scen3).

## Scenario 1: nessuna istantanea, compilazione stabile (connessione SSH disponibile) {#scen2}

Questa sezione mostra come eseguire il rollback di un ambiente quando non è stata creata una copia istantanea ma è possibile accedere all’ambiente tramite SSH.

I passaggi sono i seguenti:

1. Disabilita Gestione configurazione.
1. Disinstallare il software Adobe Commerce.
1. Reimposta il ramo Git.

Dopo aver eseguito questi passaggi:

* l’installazione di Adobe Commerce ritorna allo stato Vanilla (database ripristinato; configurazione di distribuzione rimossa; directory in `var` cancellato)
* il ramo git è reimpostato sullo stato desiderato in passato

Leggi i passaggi dettagliati seguenti:

### Passaggio 0 (prerequisito): rimuovere config.php per disabilitare Configuration Management {#disable_config_management}

È necessario disabilitare Gestione configurazione in modo che non applichi automaticamente le impostazioni di configurazione precedenti durante la distribuzione.

Per disabilitare la gestione della configurazione, assicurati che `/app/etc/` la directory non contiene `config.php` (per Adobe Commerce 2.4.x) o `config.local.php` (per Adobe Commerce 2.1.x).

Per rimuovere il file di configurazione, effettuare le seguenti operazioni:

1. [SSH per l’ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Rimuovi il file di configurazione:
   * Per Adobe Commerce 2.4:

   ```php
    rm app/etc/config.php
   ```

   * Per Adobe Commerce 2.1:

   ```php
     rm app/etc/config.local.php
   ```

Per ulteriori informazioni sulla gestione della configurazione, consulta:

* [Riduzione dei tempi di inattività dell&#39;implementazione su Adobe Commerce su infrastruttura cloud](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md) nella nostra knowledge base di supporto.
* [Gestione della configurazione per le impostazioni dello store](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) nella documentazione per gli sviluppatori.

### Passaggio 1: disinstallare il software Adobe Commerce con il comando setup:uninstall {#setup-uninstall}


La disinstallazione del software Adobe Commerce fa cadere e ripristina il database, rimuove la configurazione di distribuzione e cancella le directory in `var`.

Revisione [Disinstallare il software Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall.html) nella documentazione per gli sviluppatori.

Per disinstallare il software Adobe Commerce, effettuare le seguenti operazioni:

1. [SSH per l’ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
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

1. Clona l’ambiente nell’ambiente di sviluppo locale. Puoi copiare il comando nella console Cloud:    ![copy_git_clone.png](assets/copy_git_clone.png)
1. Accedi alla cronologia dei commit. Utilizzare `--reverse` per visualizzare la cronologia in ordine inverso per maggiore comodità:

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

[1. Reimposta il ramo Git.](/help/how-to/general/reset-environment-on-cloud.md#reset-git-branch)

[2. Disabilita Gestione configurazione.](/help/how-to/general/reset-environment-on-cloud.md#disable_config_management)

[3. Disinstallare il software Adobe Commerce.](/help/how-to/general/reset-environment-on-cloud.md#setup-uninstall)

4&amp;period; Forza la ridistribuzione.

Dopo aver eseguito questi passaggi, si otterranno gli stessi risultati dello Scenario 1.

### Passaggio 4: forzare la ridistribuzione

Esegui un commit (potrebbe essere vuoto, anche se non è consigliato) e invialo al server per attivarne la ridistribuzione:

```git
git commit --allow-empty -m "<message>" && git push <origin> <branch>
```

## Se l&#39;installazione:disinstallazione non riesce, reimpostare il database manualmente

Se si esegue `setup:uninstall` Il comando ha esito negativo e non può essere completato. È possibile che il DB venga cancellato manualmente con i seguenti passaggi:

1. [SSH per l’ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Connettersi al database MySQL:

   ```sql
   mysql -h database.internal
   ```

1. Rilascia il `main` DB:

   ```sql
   drop database main;
   ```

1. Crea un elemento vuoto `main` DB:

   ```sql
   create database main;
   ```

1. Elimina i seguenti file di configurazione: `config.php`, `config.php` `.bak`, `env.php`, e `env.php.bak`.

Dopo aver ripristinato il DB, [effettua un push Git nell’ambiente per attivare la ridistribuzione](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html#git-commands) e installare Adobe Commerce in un database appena creato. Oppure [eseguire il comando ridistribuisci](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html#environment-commands).

## Lettura correlata

Nella documentazione per gli sviluppatori:

* [Ripristinare una copia istantanea nel cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#restore-a-manual-backup)
* [Creare un’istantanea](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#create-a-manual-backup)
* [Snapshot e gestione dei backup](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots)
* [Gestire i rami con Cloud Console: visualizza i registri](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/console-branches.html?lang=en#view-logs)
* [Errore di distribuzione del componente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/recover-failed-deployment.html)
* [Gestione del progetto](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html#configure-the-project)
