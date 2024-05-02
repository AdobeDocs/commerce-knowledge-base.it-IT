---
title: Dopo l'installazione, le immagini e i fogli di stile non vengono caricati; vengono visualizzati solo testo, senza elementi grafici
description: Questo articolo descrive i possibili motivi e soluzioni del problema che si verifica quando i fogli di stile e le immagini non vengono caricati dopo l’installazione di Adobe Commerce.
exl-id: f33cee89-b416-4d63-8cc5-9cc57618ce92
feature: Install, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---

# Dopo l&#39;installazione, le immagini e i fogli di stile non vengono caricati; vengono visualizzati solo testo, senza elementi grafici

Questo articolo descrive i possibili motivi e soluzioni del problema che si verifica quando i fogli di stile e le immagini non vengono caricati dopo l’installazione di Adobe Commerce.

## Prodotti e versioni interessati

* Adobe Commerce 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x

## Problema

<u>Passaggi da riprodurre</u>

1. Installa Adobe Commerce.
1. Passa alla vetrina o all’amministratore.

<u>Risultato previsto</u>

Gli stili vengono applicati, nessun elemento dell’interfaccia utente ha l’aspetto di stili mancanti.

<u>Risultato effettivo</u>

Gli stili non vengono applicati correttamente, manca la grafica.

## Causa

Il percorso delle immagini e dei fogli di stile non è corretto, a causa di un URL di base non corretto o perché le riscritture del server (CentOS, Ubuntu) non sono configurate correttamente.

Per confermare questo caso, utilizza una finestra di ispezione del browser web per controllare i percorsi delle risorse statiche e verificare che si trovino sul file system di Adobe Commerce o di Magento Open Source.

Le risorse statiche si trovano in `<magento_root>/pub/static/` , all&#39;interno del `frontend` e `adminhtml` directory.

## Soluzione

Di seguito sono riportate le possibili soluzioni in base al software utilizzato e alla causa del problema:

* Se utilizzi il server web Apache, verifica i [riscritture server](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/apache.html#apache-help-rewrite) e l’URL di base del server Adobe Commerce/Magento Open Source e riprova. Se imposti Apache `AllowOverride` direttiva non correttamente, i file statici non vengono trasmessi dalla posizione corretta.
* Se utilizzi il server web Inginx, assicurati di [configurare un file host virtuale](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/nginx.html#configure-nginx-ubuntu). Il file host virtuale nginx deve soddisfare i seguenti criteri:
   * Il `include` la direttiva deve puntare al file di configurazione nginx di esempio nella directory di installazione di Adobe Commerce/Magento Open Source. Ad esempio:    `include /var/www/html/magento2/nginx.conf.sample;`
   * Il `server_name` La direttiva deve corrispondere all’URL di base specificato durante l’installazione di Adobe Commerce/Magento Open Source. Ad esempio: `server_name 192.186.33.10;`
* Se l’applicazione è in [modalità di produzione](https://devdocs.magento.com/guides/v2.3/config-guide/bootstrap/magento-modes.html#production-mode), provare a distribuire i file di visualizzazione statica utilizzando `magento setup:static-content:deploy` comando. Per informazioni dettagliate sulla distribuzione di file statici, fare riferimento a [Distribuire file di visualizzazione statica](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-subcommands-maint.html) nella documentazione per gli sviluppatori.
