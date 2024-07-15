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

Le risorse statiche si trovano in `<magento_root>/pub/static/` , nelle directory `frontend` e `adminhtml`.

## Soluzione

Di seguito sono riportate le possibili soluzioni in base al software utilizzato e alla causa del problema:

* Se utilizzi il server web Apache, verifica che l&#39;impostazione [server riscriva](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/apache.html#apache-help-rewrite) e l&#39;URL di base del server Adobe Commerce/Magento Open Source e riprova. Se la direttiva Apache `AllowOverride` non è stata configurata correttamente, i file statici non vengono distribuiti dalla posizione corretta.
* Se si utilizza il server Web nginx, [configurare un file host virtuale](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/nginx.html#configure-nginx-ubuntu). Il file host virtuale nginx deve soddisfare i seguenti criteri:
   * La direttiva `include` deve puntare al file di configurazione nginx di esempio nella directory di installazione di Adobe Commerce/Magento Open Source. Ad esempio:    `include /var/www/html/magento2/nginx.conf.sample;`
   * La direttiva `server_name` deve corrispondere all&#39;URL di base specificato durante l&#39;installazione di Adobe Commerce/Magento Open Source. Esempio: `server_name 192.186.33.10;`
* Se l&#39;applicazione è in [modalità di produzione](https://devdocs.magento.com/guides/v2.3/config-guide/bootstrap/magento-modes.html#production-mode), provare a distribuire i file di visualizzazione statica utilizzando il comando `magento setup:static-content:deploy`. Per informazioni dettagliate sulla distribuzione di file statici, consultare [Distribuire file di visualizzazione statici](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-subcommands-maint.html) nella documentazione per gli sviluppatori.
