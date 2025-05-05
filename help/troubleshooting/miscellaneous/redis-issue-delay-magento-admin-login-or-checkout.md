---
title: Il problema Redis ritarda l’accesso o il pagamento dell’amministratore di Commerce
description: Questo articolo fornisce una correzione del problema che si verifica quando si accede all’amministratore di Commerce o si apre la pagina di pagamento e causa un ritardo o un timeout (oltre 30 secondi). Il problema si verifica quando Redis viene utilizzato per l’archiviazione della sessione.
exl-id: a91a7a51-7cc4-4910-a9de-3a212788663f
feature: Admin Workspace, Checkout, Orders, Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# Il problema Redis ritarda l’accesso o il pagamento dell’amministratore di Commerce

Questo articolo fornisce una correzione del problema che si verifica quando si accede all’amministratore di Commerce o si apre la pagina di pagamento e causa un ritardo o un timeout (oltre 30 secondi). Il problema si verifica quando Redis viene utilizzato per l’archiviazione della sessione.

**Causa:**   [Problema Github \#12385](https://github.com/magento/magento2/issues/12385).

**Soluzione:** aggiornamento alla patch Adobe Commerce più recente per risolvere questi problemi per tutte le versioni di Redis e per le versioni specifiche di Adobe Commerce.

## Versioni e tecnologie interessate

* Adobe Commerce sulle versioni 2.1.11 - 2.1.13 e 2.2.1 dell’infrastruttura cloud
* Adobe Commerce on-premise versioni 2.1.11 - 2.1.13 e 2.2.1
* Redis, tutte le versioni

Se si utilizza Adobe Commerce nella versione [2.2.0](#h_64593789291526919876198) dell&#39;infrastruttura cloud, è disponibile una soluzione alternativa.

## Problema

L’accesso all’amministratore di Commerce o l’avanzamento alla pagina di pagamento richiede oltre 30 secondi.

Ciò si verifica solo quando le sessioni utente sono memorizzate in Redis.

## Causa

Adobe Commerce ha riscontrato un problema con il meccanismo di blocco delle sessioni che ha aggiunto un timeout di 30 secondi ad alcune operazioni quando Redis veniva utilizzato per l’archiviazione delle sessioni. Per informazioni dettagliate, consulta il [problema Github \#12385](https://github.com/magento/magento2/issues/12385).

Questo problema è stato risolto in Adobe Commerce 2.1.14 e 2.2.2.

## Soluzioni: patch o aggiornamento

### Soluzione 1: applicare la patch con una correzione

Per ricevere una patch, [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) richiedendo la patch. Nel ticket, specifica la versione di Adobe Commerce e il numero di riferimento corrispondente per la patch:

* **2.1.11 e versioni successive:** MDVA-7835
* **2.2.1:** MDVA-8128

Il numero di riferimento generale (indipendente dalla versione) è MAGETWO-84289.

### Soluzione 2: eseguire l&#39;aggiornamento a 2.1.14/2.2.2 o versione successiva

Se in precedenza hai preso in considerazione l’aggiornamento a Adobe Commerce 2.2.2 o versione successiva, puoi utilizzare questa opportunità di aggiornamento per risolvere il problema.

## Soluzione alternativa: disattivare il blocco della sessione

Per disattivare il blocco della sessione, impostare `disable_locking` su `1` nella sezione di configurazione Redis del file `env.php`:

```php
'session' =>
  array (
    'save' => 'redis',
    'redis' =>
    array (
      'host' => 'redis.internal',
      'port' => 6379,
      'database' => '0',
      'disable_locking' => '1'
    ),
  ),
```

Questa soluzione non influisce su altre funzionalità di Adobe Commerce.

### Ripristina soluzione alternativa dopo l’applicazione della patch

Dopo l&#39;applicazione della patch con la correzione, la soluzione alternativa non è più necessaria, pertanto è possibile ripristinarla (impostare `disable_locking` su `0`).

## Adobe Commerce su infrastruttura cloud 2.2.0: utilizzare ECE-Tools v2002.0.8 o versione successiva {#h_64593789291526919876198}

Il pacchetto di script di distribuzione [ECE-Tools](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package) con versioni 2002.0.3 - 2002.0.7 [applica](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html?lang=it) automaticamente la soluzione alternativa, impostando `disable_locking` su `1`. Questo disattiva il meccanismo di blocco della sessione per Adobe Commerce 2.2.0, in cui non si verifica il problema originale.

Se esegui Adobe Commerce su infrastruttura cloud 2.2.0, aggiorna ECE-Tools alla versione v2002.0.8 successiva. Puoi anche valutare la possibilità di aggiornare l’infrastruttura cloud di Adobe Commerce alla versione 2.2.2 o successiva.
