---
title: Le modifiche nel database non si riflettono nella vetrina
description: Questo articolo fornisce soluzioni per evitare ritardi o interruzioni nell’applicazione degli aggiornamenti delle entità. Ciò include come evitare che le tabelle di registro delle modifiche vengano sovradimensionate e come impostare i trigger di tabella MySQL.
exl-id: ac52c808-299f-4d08-902f-f87db1fa7ca6
feature: Catalog Management, Categories, Services, Storefront
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---

# Le modifiche nel database non si riflettono nella vetrina

Questo articolo fornisce soluzioni per evitare ritardi o interruzioni nell’applicazione degli aggiornamenti delle entità. Ciò include come evitare che le tabelle di registro delle modifiche vengano sovradimensionate e come impostare i trigger di tabella MySQL.

Prodotti e versioni interessati:

* Adobe Commerce sull’infrastruttura cloud 2.2.x, 2.3.x
* Adobe Commerce on-premise 2.2.x, 2.3.x

## Problema

Le modifiche apportate nel database non vengono applicate nella vetrina, oppure si verifica un ritardo significativo nell’applicazione degli aggiornamenti delle entità. Le entità che potrebbero essere interessate includono prodotti, categorie, prezzi, scorte, regole di catalogo, regole di vendita e regole target.

## Causa

Se gli indicizzatori sono [configurati per l&#39;aggiornamento in base alla pianificazione](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-index.html#configure-indexers), il problema potrebbe essere causato da una o più tabelle con log delle modifiche troppo grandi o da trigger MySQL non configurati.

### Tabelle di log delle modifiche sovradimensionate

Le dimensioni delle tabelle del registro delle modifiche aumentano se il processo cron `indexer_update_all_views` non viene completato più volte.

Le tabelle di log delle modifiche sono le tabelle di database in cui vengono tracciate le modifiche apportate alle entità. Un record viene archiviato in una tabella del registro delle modifiche finché la modifica non viene applicata, operazione eseguita dal processo cron `indexer_update_all_views`. In un database Adobe Commerce sono presenti più tabelle di log delle modifiche denominate in base al seguente pattern: INDEXER\_TABLE\_NAME + ‘\_cl’, ad esempio `catalog_category_product_cl`, `catalog_product_category_cl`. Per ulteriori dettagli sul tracciamento delle modifiche nel database, consulta l&#39;articolo [Panoramica sull&#39;indicizzazione > Mview](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/indexing.html#m2devgde-mview) nella documentazione per gli sviluppatori.

### I trigger del database MySQL non sono configurati

Si può sospettare che i trigger del database non siano configurati, se dopo l&#39;aggiunta o la modifica di un&#39;entità (prodotto, categoria, regola di destinazione e così via) - non vengono aggiunti record alla tabella del log delle modifiche corrispondente.

## Soluzione

>[!WARNING]
>
>Si consiglia vivamente di creare un backup del database prima di eseguire eventuali manipolazioni, evitando di eseguirle durante periodi di caricamento elevati del sito.

### Evitare che le tabelle del registro delle modifiche vengano sovradimensionate

Verificare che il processo cron `indexer_update_all_views` sia sempre completato correttamente.

È possibile utilizzare la query SQL seguente per ottenere tutte le istanze non riuscite del processo cron `indexer_update_all_views`:

```sql
select * from cron_schedule where job_code = "indexer_update_all_views" and status
  <> "success" and status <> "pending";
```

Oppure puoi controllarne lo stato nei registri cercando le `indexer_update_all_views` voci:

* `<install_directory>/var/log/cron.log` - per le versioni 2.3.1+ e 2.2.8+
* `<install_directory>/var/log/system.log` - per versioni precedenti

### Reimposta trigger tabella MySQL

Per impostare i trigger della tabella MySQL mancanti, è necessario reimpostare la modalità di indicizzazione:

1. Passa a &quot;Al salvataggio&quot;.
1. Torna a &quot;In programma&quot;.

Utilizzare il comando seguente per eseguire questa operazione.

>[!WARNING]
>
>Prima di cambiare modalità di indicizzazione, è consigliabile attivare la modalità [manutenzione](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html#maintenance-mode) del sito Web e [disabilitare i processi cron](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#disable-cron-jobs) per evitare blocchi del database.

```bash
php bin/magento indexer:set-mode {realtime|schedule} [indexerName]
```

>[!INFO]
>
>I trigger del database relativi agli indicizzatori vengono aggiunti quando la modalità di indicizzazione è impostata su Pianifica e rimossi quando la modalità di indicizzazione è impostata su In tempo reale. Se i trigger non sono presenti nel database mentre gli indicizzatori sono impostati per la pianificazione, modificare gli indicizzatori in tempo reale e quindi riportarli alla pianificazione. In questo modo vengono ripristinati i trigger.

## Lettura correlata

<ul><li title="Le tabelle MySQL sono troppo grandi"><a href="/help/troubleshooting/database/mysql-tables-are-too-large.md">Le tabelle MySQL sono troppo grandi</a> nella Knowledge Base di supporto.</li>
<li title="Le tabelle MySQL sono troppo grandi"><a href="https://devdocs.magento.com/guides/v2.3/extension-dev-guide/indexing.html#m2devgde-mview">Panoramica dell'indicizzatore &gt; Mview</a> nella documentazione per gli sviluppatori.</li></ul>
