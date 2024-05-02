---
title: Risolvi i problemi relativi alla chiave di crittografia
description: Questo articolo illustra come risolvere i problemi causati dal mancato spostamento della chiave di crittografia insieme all’immagine del database nell’altro ambiente.
exl-id: 34410da0-1bd5-421e-9cd7-d3ee75ad8ed7
feature: Cache, Variables
role: Developer
source-git-commit: bee0263da487399ab07bf9158c4d60ab316d6ea1
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---

# Risolvi i problemi relativi alla chiave di crittografia

Questo articolo illustra come risolvere i problemi causati dal mancato spostamento della chiave di crittografia insieme all’immagine del database nell’altro ambiente.

## Prodotti e versioni interessati

* Adobe Commerce sull’infrastruttura cloud 2.2.x, 2.3.x

## Problema

Dopo l’importazione di un [dump del database](/help/how-to/general/create-database-dump-on-cloud.md) dagli ambienti di produzione agli ambienti di staging/integrazione, i numeri delle carte di credito salvate appaiono errati e/o i pagamenti non riescono per le integrazioni di pagamento che richiedono l’utilizzo di credenziali esercente.

## Causa

La chiave di crittografia utilizzata per crittografare i dati sensibili, come i numeri di carta di credito e le credenziali dell’esercente, non viene memorizzata nel database e pertanto non viene trasferita in un altro ambiente dopo l’importazione/esportazione del dump del database.

## Soluzione

È necessario copiare la chiave di crittografia dall&#39;ambiente di origine e aggiungerla all&#39;ambiente di destinazione.

Per copiare la chiave di crittografia:

1. SSH al progetto di origine dell’immagine del database, come descritto in [SSH nell’ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) nella documentazione per gli sviluppatori.
1. Apri `app/etc/env.php` in un editor di testo.
1. Copia il valore di `key` per `crypt`.

```php
return array ('crypt' =>      array ('key' => '<your encryption key>', ),);
```

Per impostare il valore chiave per il progetto di destinazione:

1. Apri [Console cloud](https://console.adobecommerce.com) e individua il progetto.
1. Imposta il valore del [CRYPT\_KEY](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html) (nella documentazione per gli sviluppatori), come descritto in [Configurare il progetto](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html) nella documentazione per gli sviluppatori. Questo attiverà il processo di distribuzione e `CRYPT_KEY` verrà sovrascritto in `app/etc/env.php` su ogni distribuzione.

Facoltativamente, puoi sovrascrivere manualmente la chiave di crittografia nel `app/etc/env.php` file:

1. SSH all’ambiente di destinazione.
1. Apri `app/etc/env.php` in un editor di testo.
1. Incolla i dati copiati come `key` valore per `crypt`.
1. Salva il file modificato `env.php`.
1. Pulizia della cache nell’ambiente di destinazione tramite l’esecuzione di `bin/magento cache:clean` o in Commerce Admin in **Sistema** > **Strumenti** > **Gestione cache**.
