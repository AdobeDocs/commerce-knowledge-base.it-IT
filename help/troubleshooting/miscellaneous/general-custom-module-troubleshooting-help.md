---
title: Guida generale alla risoluzione dei problemi dei moduli personalizzati
description: Questo articolo descrive gli strumenti generali per la risoluzione dei problemi dei moduli personalizzati in Adobe Commerce.
exl-id: c6603a2b-dc98-4022-ab29-c081c2b07415
feature: Extensions
role: Developer
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# Guida generale alla risoluzione dei problemi dei moduli personalizzati

Questo articolo descrive gli strumenti generali per la risoluzione dei problemi dei moduli personalizzati in Adobe Commerce.

## Problema

Se ti rendi conto che esiste un problema con le funzioni del modulo personalizzato e non ricevi messaggi di errore evidenti che segnalano il problema, allora vorrai consultare i registri della tua istanza.

## Soluzione

Controlla i registri per verificare se nell’errore sono presenti voci con il nome del modulo personalizzato.  A seconda degli errori coinvolti, la soluzione potrebbe presentarsi da sola o potrebbe essere necessario includere le informazioni utili del registro di Adobe Commerce se si desidera aprire un [ticket di supporto](https://experienceleague.adobe.com/it/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket). Consulta i paragrafi seguenti per informazioni sulla posizione dei registri e sulle possibili soluzioni.

### Adobe Commerce (tutti i metodi di distribuzione), Magento Open Source, tutte le versioni 2.X

1. La posizione dei registri si trova in [Adobe Commerce sui registri dell&#39;architettura del piano Pro dell&#39;infrastruttura cloud](/help/how-to/general/log-locations-directories-for-pro-plan-integration-staging-production.md) nella knowledge base del supporto.
1. A seconda degli errori rilevati, se si desidera abilitare, disabilitare o disinstallare un modulo personalizzato, questi articoli descrivono nel dettaglio le azioni seguenti:
   * [Abilita o disabilita i moduli](https://experienceleague.adobe.com/it/docs/commerce-operations/installation-guide/tutorials/manage-modules) nella documentazione per gli sviluppatori.
   * [Disinstallare i moduli](https://experienceleague.adobe.com/it/docs/commerce-operations/installation-guide/tutorials/uninstall-modules) nella documentazione per gli sviluppatori.

### Adobe Commerce su infrastruttura cloud, tutte le versioni

1. Percorsi dei registri: [Adobe Commerce nei registri dell&#39;infrastruttura cloud](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/test/log-locations) nella documentazione per gli sviluppatori.
1. A seconda degli errori rilevati, se desideri abilitare, disabilitare o disinstallare un modulo personalizzato, questi articoli nella documentazione per gli sviluppatori descrivono nel dettaglio tali azioni:
   * [Installare, gestire e aggiornare le estensioni](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/configure-store/extensions).
   * [Errore di distribuzione del componente](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/deploy/recover-failed-deployment).

## Lettura correlata

Nella documentazione per gli sviluppatori:

* [Panoramica modulo](https://developer.adobe.com/commerce/php/architecture/modules/overview/)
* [Errori durante l&#39;installazione dei dati di esempio facoltativi](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/errors-installing-optional-sample-data)
* [Gestione delle eccezioni](https://developer.adobe.com/commerce/webapi/graphql/develop/exceptions/)
* [Eccezioni durante l&#39;installazione](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/exceptions-during-installation)
* [Esegui Gestione moduli](https://experienceleague.adobe.com/it/docs/commerce-operations/upgrade-guide/prepare/prerequisites)
* [File di configurazione modulo](https://experienceleague.adobe.com/it/docs/commerce-operations/configuration-guide/files/module-files)
* [Errori di memoria insufficiente](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/out-of-memory-error-during-install-or-upgrade)
