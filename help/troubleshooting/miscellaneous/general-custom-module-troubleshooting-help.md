---
title: Guida generale alla risoluzione dei problemi dei moduli personalizzati
description: Questo articolo descrive gli strumenti generali per la risoluzione dei problemi dei moduli personalizzati in Adobe Commerce.
exl-id: c6603a2b-dc98-4022-ab29-c081c2b07415
feature: Extensions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# Guida generale alla risoluzione dei problemi dei moduli personalizzati

Questo articolo descrive gli strumenti generali per la risoluzione dei problemi dei moduli personalizzati in Adobe Commerce.

## Problema

Se ti rendi conto che esiste un problema con le funzioni del modulo personalizzato e non ricevi messaggi di errore evidenti che segnalano il problema, allora vorrai consultare i registri della tua istanza.

## Soluzione

Controlla i registri per verificare se nell’errore sono presenti voci con il nome del modulo personalizzato.  A seconda degli errori coinvolti, la soluzione potrebbe presentarsi da sola o potrebbe essere necessario includere le informazioni utili del registro di Adobe Commerce se si desidera aprire un [ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket). Consulta i paragrafi seguenti per informazioni sulla posizione dei registri e sulle possibili soluzioni.

### Adobe Commerce (tutti i metodi di distribuzione), Magento Open Source, tutte le versioni 2.X

1. Posizioni dei registri:
   * [Adobe Commerce sull&#39;infrastruttura cloud Registri dell&#39;architettura del piano di avvio](/help/how-to/general/log-locations-directories-for-starter-plan.md) nella knowledge base di supporto.
   * [Registri dell&#39;architettura del piano Pro di Adobe Commerce su infrastruttura cloud](/help/how-to/general/log-locations-directories-for-pro-plan-integration-staging-production.md) nella knowledge base del supporto.
1. A seconda degli errori rilevati, se si desidera abilitare, disabilitare o disinstallare un modulo personalizzato, questi articoli descrivono nel dettaglio le azioni seguenti:
   * [Abilita o disabilita i moduli](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-subcommands-enable.html) nella documentazione per gli sviluppatori.
   * [Disinstallare i moduli](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-uninstall-mods.html) nella documentazione per gli sviluppatori.

### Adobe Commerce su infrastruttura cloud, tutte le versioni

1. Percorsi dei registri: [Adobe Commerce nei registri dell&#39;infrastruttura cloud](https://devdocs.magento.com/guides/v2.3/cloud/trouble/environments-logs.html) nella documentazione per gli sviluppatori.
1. A seconda degli errori rilevati, se desideri abilitare, disabilitare o disinstallare un modulo personalizzato, questi articoli nella documentazione per gli sviluppatori descrivono nel dettaglio tali azioni:
   * [Installare, gestire e aggiornare le estensioni](https://devdocs.magento.com/guides/v2.3/cloud/howtos/install-components.html).
   * [Errore di distribuzione del componente](https://devdocs.magento.com/guides/v2.3/cloud/trouble/trouble_comp-deploy-fail.html).

## Lettura correlata

Nella documentazione per gli sviluppatori:

* [Panoramica modulo](https://devdocs.magento.com/guides/v2.3/architecture/archi_perspectives/components/modules/mod_intro.html)
* [Errori durante l&#39;installazione dei dati di esempio facoltativi](https://devdocs.magento.com/guides/v2.3/install-gde/trouble/tshoot_sample-data.html)
* [Gestione delle eccezioni](https://devdocs.magento.com/guides/v2.3/graphql/develop/exceptions.html)
* [Eccezioni durante l&#39;installazione](https://devdocs.magento.com/guides/v2.3/install-gde/trouble/tshoot_exceptions.html)
* [Esegui Gestione moduli](https://devdocs.magento.com/guides/v2.3/comp-mgr/module-man/compman-checklist.html)
* [File di configurazione modulo](https://devdocs.magento.com/guides/v2.3/config-guide/config/config-files.html)
* [Errori di memoria insufficiente](https://devdocs.magento.com/guides/v2.3/comp-mgr/trouble/cman/out-of-memory.html)
