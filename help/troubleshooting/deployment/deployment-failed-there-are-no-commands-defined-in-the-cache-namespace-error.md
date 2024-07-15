---
title: "Distribuzione non riuscita: nessun comando definito nell'errore dello spazio dei nomi 'cache'"
description: Questo articolo fornisce una soluzione al problema quando la distribuzione non riesce con il seguente errore **Non sono stati definiti comandi nello spazio dei nomi della cache**.
feature: Deploy
role: Developer
exl-id: ee2bddba-36f7-4aae-87a1-5dbeb80e654e
source-git-commit: 1a8a4e1eada859a6712a43536d7bad26d1ce1244
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# Distribuzione non riuscita: nessun comando definito nell&#39;errore dello spazio dei nomi &#39;cache&#39;

>[!WARNING]
>
>Esegui il backup del database prima di eseguire questi passaggi, se lo stai facendo in un sito di produzione live.

Questo articolo fornisce una soluzione al problema che si verifica in caso di errore di distribuzione e uno degli errori nel registro è simile al seguente:

```
[YEAR-DAYTIME] ERROR: [127] The command "php ./bin/magento cache:flush --ansi --no-interaction" failed.
        There are no commands defined in the "cache" namespace.
...
      W:     There are no commands defined in the "cache" namespace.
```

## Prodotti e versioni interessati

Adobe Commerce sull’infrastruttura cloud 2.4.x

## Problema  

<u>Passaggi da riprodurre</u>:

Tentativo di distribuzione. 

<u>Risultati previsti</u>:

Distribuzione completata.

<u>Risultati effettivi</u>:

La distribuzione non è riuscita. Nei registri viene visualizzato un errore di distribuzione con un messaggio simile al seguente *Nessun comando nello spazio dei nomi della cache*.

### Causa

La tabella **core_config_data** contiene le configurazioni per un ID archivio o un ID sito Web che non esiste più nel database. Ciò si verifica quando si importa un backup del database da un&#39;altra istanza o da un altro ambiente e le configurazioni per tali ambiti rimangono nel database anche se gli store o i siti Web associati sono stati eliminati.

### Soluzione

Se disponi di un solo sito web, il secondo test per i siti web non è applicabile e devi solo verificare la presenza di negozi.

Per risolvere questo problema, identifica le righe non valide rimaste da tali configurazioni.

1. SSH al server ed eseguire il comando seguente:

   `bin/magento`

1. Il messaggio di errore può indicare quali righe e tabelle rimangono nel database dai siti eliminati. Ad esempio, di seguito è riportato un errore che indica che l’archivio richiesto non è stato trovato:

   ```...
   In StoreRepository.php line 112:
   
   The store that was requested wasn't found. Verify the store and try again.
   ```

1. Eseguire questa query MySql per verificare che non sia possibile trovare l&#39;archivio, indicato dal messaggio di errore nel passaggio 2. 

   ```sql
   select distinct scope_id from core_config_data where scope='stores' and scope_id not in (select store_id from store);
   ```

1. Eseguire la seguente istruzione MySql per eliminare le righe non valide: 

   ```sql
   delete from core_config_data where scope='stores' and scope_id not in (select store_id from store); 
   ```

1. Esegui di nuovo questo comando:

   `bin/magento`

   Se ricevi un errore simile al seguente che indica che il sito web con ID X richiesto non è stato trovato, sono presenti configurazioni rimanenti        nel database dai siti Web e dai negozi che sono stati eliminati.

   ```
   In WebsiteRepository.php line 110:
   
   The website with id X that was requested wasn't found. Verify the website and try again.
   ```

   Eseguire questa query MySQL e verificare che il sito Web non sia stato trovato:

   ```sql
   select distinct scope_id from core_config_data where scope='stores' and scope_id not in (select store_id from store);
   ```

1. Eseguire questa istruzione MySql per eliminare le righe non valide dalla configurazione del sito Web:

   ```sql
   delete from core_config_data where scope='websites' and scope_id not in (select website_id from store_website);
   ```

Per verificare che la soluzione funzioni, eseguire di nuovo il comando `bin/magento`. Gli errori non dovrebbero più essere visualizzati e la distribuzione può essere eseguita correttamente.

## Lettura correlata

* [Risoluzione dei problemi di distribuzione di Adobe Commerce](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-deployment-troubleshooter.html)
* [Verifica del registro di distribuzione se nell’interfaccia utente di Cloud è presente l’errore &quot;log snipped&quot;](/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error.html)
