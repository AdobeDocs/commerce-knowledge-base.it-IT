---
title: Risolvi i problemi relativi alla chiave di crittografia
description: Questo articolo illustra come risolvere i problemi causati dal mancato spostamento della chiave di crittografia insieme all’immagine del database nell’altro ambiente.
exl-id: 34410da0-1bd5-421e-9cd7-d3ee75ad8ed7
feature: Cache, Variables
role: Developer
source-git-commit: 0458b37e2af4c9ad2ec92a1fdd6844ef222ef84a
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# Risolvi i problemi relativi alla chiave di crittografia

Questo articolo illustra come risolvere i problemi causati dal mancato spostamento della chiave di crittografia insieme all’immagine del database nell’altro ambiente.

## Prodotti e versioni interessati

* Adobe Commerce sull’infrastruttura cloud 2.4.x

## Problema

Dopo aver importato un [dump del database](/help/how-to/general/create-database-dump-on-cloud.md) dalla produzione agli ambienti di gestione temporanea/integrazione, i numeri di carta di credito salvati appaiono errati e/o i pagamenti non riescono per le integrazioni di pagamento che richiedono l&#39;utilizzo di credenziali esercente.

## Causa

La chiave di crittografia utilizzata per crittografare i dati sensibili, come i numeri di carta di credito e le credenziali dell’esercente, non viene memorizzata nel database e pertanto non viene trasferita in un altro ambiente dopo l’importazione/esportazione del dump del database.

## Soluzione

È necessario copiare la chiave di crittografia dall&#39;ambiente di origine e aggiungerla all&#39;ambiente di destinazione.

Per copiare la chiave di crittografia:

1. SSH al progetto che era l&#39;origine per l&#39;immagine del database, come descritto in [SSH all&#39;ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=it) nella documentazione per gli sviluppatori.
1. Apri `app/etc/env.php` in un editor di testo.
1. Copia il valore di `key` per `crypt`.

```php
return array ('crypt' =>      array ('key' => '<your encryption key>', ),);
```

Per impostare il valore chiave per il progetto di destinazione:

1. Apri [Cloud Console](https://console.adobecommerce.com) e individua il progetto.
1. Imposta il valore della variabile [CRYPT\_KEY](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=it) (nella documentazione per gli sviluppatori), come descritto in [Configura il progetto](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=it) nella documentazione per gli sviluppatori. In questo modo verrà attivato il processo di distribuzione e `CRYPT_KEY` verrà sovrascritto nel file `app/etc/env.php` in ogni distribuzione.

Se necessario, è possibile sovrascrivere manualmente la chiave di crittografia nel file `app/etc/env.php`:

1. SSH all’ambiente di destinazione.
1. Apri `app/etc/env.php` in un editor di testo.
1. Incolla i dati copiati come valore `key` per `crypt`.
1. Salva `env.php` modificato.
1. Pulire la cache nell&#39;ambiente di destinazione eseguendo `bin/magento cache:clean` o nell&#39;amministratore di Commerce in **Sistema** > **Strumenti** > **Gestione cache**.
