---
title: Reindirizzamento all’ambiente principale durante l’accesso al nuovo ambiente di integrazione
description: Questo articolo fornisce istruzioni per la risoluzione del problema relativo all’infrastruttura cloud di Adobe Commerce, in cui il tentativo di accedere all’ambiente di integrazione appena creato porta all’ambiente principale.
exl-id: d1d40c8d-d43c-442e-95c9-76f3cdcafb0e
feature: Cache, Integration, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Reindirizzamento all’ambiente principale durante l’accesso al nuovo ambiente di integrazione

Questo articolo fornisce istruzioni per la risoluzione del problema relativo all’infrastruttura cloud di Adobe Commerce, in cui il tentativo di accedere all’ambiente di integrazione appena creato porta all’ambiente principale.

Per risolvere questo problema, devi correggere il valore base\_url nel database e assicurarti che il `UPDATE_URLS` il valore della variabile è impostato su `true`. Per ulteriori informazioni, consulta le sezioni seguenti.

Versioni interessate:

* Adobe Commerce sull’infrastruttura cloud 2.X.X

## Problema

<u>Passaggi da riprodurre</u>:

1. Clona il ramo di integrazione esistente.
1. Fai clic sull’URL per accedere al nuovo ambiente.

<u>Risultato previsto</u>:

Viene visualizzato l’ambiente appena creato.

<u>Risultato effettivo</u>:

Viene eseguito il reindirizzamento all’ambiente nel ramo principale.

## Soluzione

Per risolvere il problema, è necessario correggere il `base_url` (protetto e non protetto) nel database dell’ambiente personalizzato e imposta `UPDATE_URL` variabile in `.magento.env.yaml` file.

### Correggi i valori base\_url nel database

Le modifiche nel database possono essere eseguite manualmente o utilizzando Adobe Commerce CLI, se si utilizza la versione 2.2.0 o successiva.

#### Correggere manualmente i valori nel database

1. Connettersi al database.
1. Esegui i seguenti comandi:

```sql
UPDATE core_config_data SET value = %your_new_environment_unsecure_url% WHERE path="web/unsecure/base_url"
```

```sql
update core_config_data set value = %your_new_environment_secure_url% where path="web/secure/base_url"
```

#### Correggere il database utilizzando Adobe Commerce CLI (disponibile per le versioni 2.2.X)

1. Accedi come, o passa a [Proprietario file system Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/web-server/apache.html).
1. Esegui i seguenti comandi:

```bash
php <your_magento_install_dir>/bin/magento config:set web/unsecure/base_url http://example.com
php <your_magento_install_dir>/bin/magento config:set web/secure/base_url https://example.com
```

### Imposta il `UPDATE_URLS` variabile

Nella base di codice locale, nel `.magento.env.yaml` set di file:

```
 stage:
    deploy:
        UPDATE_URLS: true
```

### Cancella cache di configurazione

Per applicare le modifiche, pulire la cache di configurazione eseguendo il comando seguente:

```bash
php <your_magento_install_dir>/bin/magento cache:clean config
```

## Articolo correlato nella documentazione per gli sviluppatori:

[Distribuire le variabili](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html)
