---
title: Errori di distribuzione dall'abilitazione del modulo Bilanciatore alfa anticipato
description: Il commerciante riscontra errori di distribuzione quando utilizza il modulo Baler in un ambiente di produzione, in quanto la funzione si trova attualmente nella fase di sviluppo alpha iniziale.
exl-id: 6cdac0a5-eaeb-467d-8369-9017aed6219e
feature: Build, Deploy, Extensions, SCD, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# Errori di distribuzione dall&#39;abilitazione del modulo Bilanciatore alfa anticipato

Il commerciante riscontra errori di distribuzione quando utilizza il modulo Baler in un ambiente di produzione, in quanto la funzione si trova attualmente nella fase di sviluppo alpha iniziale.

>[!WARNING]
>
>Il bundling JavaScript Early-alpha Baler non è pronto per l’uso in produzione e viene utilizzato a proprio rischio e pericolo.

## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud 2.3.x e 2.4.x.
* Adobe Commerce on-premise 2.3.x e 2.4.x

## Problema

Si sconsiglia ai commercianti di utilizzare il modulo Baler in un ambiente di produzione, in quanto si trova attualmente nella fase iniziale di sviluppo alfa. Il suo utilizzo può causare errori di distribuzione.

<u>Passaggi da riprodurre</u>:

1. Il commerciante tenta di inserire la variabile **SCD\_USE\_BALER** nella fase di build del file `.magento.env.yaml`, che abilita il pacchetto di aggregazione Javascript di Baler.
1. Il commerciante aggiunge anche la dipendenza del compositore Baler: `"magento/module-baler": "1.0.0-alpha"` alla sezione `require` di `composer.json`.

<u>Risultato previsto</u>:

Distribuzione riuscita.

<u>Risultato effettivo</u>:

Il commerciante visualizza il seguente messaggio di errore nei registri di distribuzione sul cloud, ovvero `<project home>/var/log/cloud.log`, nella fase di distribuzione del contenuto statico:

```
[2020-08-19 12:06:12] WARNING: [1007] Baler JS bundling cannot be used because of the following issues:
        [2020-08-19 12:06:12] WARNING:  - Path to baler executable could not be found. The Node package may not be installed or may not be linked.
```

## Causa

Il modulo Baler è attualmente nella fase iniziale di sviluppo alfa e il processo di installazione dell&#39;estensione Baler è complesso.

## Soluzione

È possibile rivedere la documentazione esistente dell&#39;Alpha di Baler all&#39;indirizzo [Github/Magento/Baler/Guida introduttiva ad alpha](https://github.com/magento/baler/blob/master/docs/ALPHA.md). Tuttavia, non è pronto per l’uso in produzione e viene utilizzato a proprio rischio. Si consiglia invece di unire o raggruppare file JavaScript (JS) utilizzando il bundling integrato di Adobe Commerce (bundling di base) per l’ottimizzazione dei file.

* È possibile attivare l&#39;unione o il raggruppamento nell&#39;amministratore (l&#39;unione e il raggruppamento non possono essere abilitati contemporaneamente): **Archivi** > **Impostazioni** > **Configurazione** > **Avanzate** > **Sviluppatore** > **Impostazioni JavaScript**.
* È inoltre possibile abilitare il bundling integrato di Adobe Commerce (bundling di base) dalla riga di comando: `php -f bin/magento config:set dev/js/enable_js_bundling 1`

Per ulteriori informazioni, consulta [Ottimizzazione dei file CSS e JavaScript su Adobe Commerce nell&#39;infrastruttura cloud e Adobe Commerce on-premise](https://support.magento.com/hc/en-us/articles/360044482152).
