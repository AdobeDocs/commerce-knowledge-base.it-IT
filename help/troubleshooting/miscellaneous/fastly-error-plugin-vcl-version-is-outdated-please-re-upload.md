---
title: "Errore rapido: la versione VCL del plug-in è obsoleta. Ricarica"
description: Questo articolo fornisce una soluzione per quando viene visualizzato il messaggio "*La versione VCL del plug-in è obsoleta! Ricarica.*" in Fastly Configuration, nell’amministratore di Commerce, a causa della mancata installazione dell’ultimo modulo Fastly.
exl-id: d7870e9e-ba6b-49c2-a80c-26fb464cbae3
feature: Best Practices, Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# Errore rapido: versione VCL del plug-in obsoleta. Ricarica

Questo articolo fornisce una soluzione per quando viene visualizzato il messaggio &quot;*La versione del plug-in VCL è obsoleta. Ricarica.*&quot; in Fastly Configuration, nell’amministratore di Commerce, perché non è stato installato il modulo Fastly più recente.

## Prodotti e versioni interessati

Adobe Commerce sull’infrastruttura cloud 2.2.x., 2.3.x<br>
Fastly: questo errore può interessare tutte le versioni del modulo Fastly eccetto l’ultima. Per informazioni sull’ultima versione, consulta [Note sulla versione più recente](https://github.com/fastly/fastly-magento2/releases) su GitHub.

## Problema

1. Accedi al pannello di amministrazione di Commerce.
1. Accedi a **Negozi** > **Configurazione** > **Avanzate** > **Sistema** > **Cache a pagina intera**   **Fastly Cache.**
1. In **Caricamento automatico e attivazione del servizio** sezione, sarà presente un’ &quot;*La versione del plug-in VCL è obsoleta. Ricarica.*&quot; notifica.
1. Si tenta di caricare i snippet VCL facendo clic sul pulsante &quot;Carica VCL in Fastly&quot;, ma viene comunque visualizzato l&#39;avviso &quot;*La versione del plug-in VCL è obsoleta. Ricarica.*&quot;

## Causa

L’estensione Fastly è stata aggiornata (insieme a una configurazione VCL in bundle e modelli), ma la configurazione VCL aggiornata non è stata caricata nel servizio Fastly. Quando aggiorni il modulo Adobe Commerce `Fastly_Cdn`, devi caricare di nuovo una configurazione VCL aggiornata in Fastly.

## Soluzione

1. Verificare di avere installato gli strumenti ECE più recenti e al [versione corrente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html) nella documentazione per gli sviluppatori. ECE-Tools ha una versione del pacchetto Fastly nelle sue dipendenze.

   Questa potrebbe non essere la versione più recente del plug-in Fastly, ma è probabile che sia una versione successiva a quella attualmente installata ed è consigliabile installare gli strumenti ECE più recenti.

1. Se non siete nella versione corrente di ECE-Tools, seguite questi passaggi per [aggiornamento](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html) nella documentazione per gli sviluppatori.
1. Dopo aver aggiornato ECE-Tools, verificare di disporre di una versione corrente di [Plugin Fastly](https://github.com/fastly/fastly-magento2/tree/master/etc/vcl_snippets) installato.
1. Se la versione del plug-in Fastly non è la versione corrente, eseguire la procedura seguente per [aggiornare il plug-in alla versione più recente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#upgrade-the-fastly-module) nella documentazione per gli sviluppatori.

## Lettura correlata

* Per informazioni sulla configurazione di Fastly, vedere [Configurare i servizi Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html) nella documentazione per gli sviluppatori.
* Per informazioni generali su Fastly, vedere [fastly.com](https://www.fastly.com/).
