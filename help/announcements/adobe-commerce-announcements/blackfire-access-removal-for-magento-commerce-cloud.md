---
title: Blackfire rimozione dell’accesso per Adobe Commerce sull’infrastruttura cloud
description: A partire dall’11 aprile 2020, l’accesso gratuito al monitoraggio delle prestazioni Blackfire non sarà più incluso in Adobe Commerce on cloud infrastructure Pro plan architecture o Adobe Commerce on cloud infrastructure Starter plan architecture subscriptions.  Non potrai più accedere al tuo account di Blackfire. È possibile continuare a utilizzare Blackfire anche dopo l'11 aprile acquistando una licenza direttamente tramite Blackfire.io. I commercianti Adobe Commerce che non hanno acquistato licenze direttamente da Blackfire entro tale data avranno le loro licenze Blackfire gratuite fornite dall’Adobe disattivate. Inoltre, la funzionalità di creazione di nuovi rapporti tramite lo strumento Profiler verrà disabilitata. I clienti che utilizzano l’architettura Pro ospitata su un’infrastruttura cloud possono ancora ricevere il monitoraggio gratuito delle prestazioni dell’infrastruttura tramite l’infrastruttura New Relic.
exl-id: bf33c2c6-e9b3-474a-a127-909b51dff92f
feature: Cloud, Paas
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# Blackfire rimozione dell’accesso per Adobe Commerce sull’infrastruttura cloud

A partire dall’11 aprile 2020, l’accesso gratuito al monitoraggio delle prestazioni Blackfire non sarà più incluso in Adobe Commerce on cloud infrastructure Pro plan architecture o Adobe Commerce on cloud infrastructure Starter plan architecture subscriptions.  Non potrai più accedere al tuo account di Blackfire. È possibile continuare a utilizzare Blackfire anche dopo l&#39;11 aprile acquistando una licenza direttamente tramite Blackfire.io. I commercianti Adobe Commerce che non hanno acquistato licenze direttamente da Blackfire entro tale data avranno le loro licenze Blackfire gratuite fornite dall’Adobe disattivate. Inoltre, la funzionalità di creazione di nuovi rapporti tramite lo strumento Profiler verrà disabilitata. I clienti che utilizzano l’architettura Pro ospitata su un’infrastruttura cloud possono ancora ricevere il monitoraggio gratuito delle prestazioni dell’infrastruttura tramite l’infrastruttura New Relic.

**Per continuare a utilizzare Blackfire**:

1. È necessario acquistare una licenza direttamente con Blackfire.
1. Quindi imposta Blackfire utilizzando questi [passaggi](https://blackfire.io/docs/integrations/paas/magentocloud).
1. In caso di problemi durante l&#39;installazione, è possibile [inviare un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) per richiedere assistenza. Per domande specifiche sulle Blackfire, contatta il supporto Blackfire direttamente all&#39;indirizzo [support@blackfire.io](mailto:support@blackfire.io).

## In caso di errori durante l’esecuzione di una distribuzione:

Se durante l’esecuzione di una distribuzione si verificano errori correlati alle Blackfire, effettua le seguenti operazioni:

1. Rimuovi Blackfire dalla configurazione. Modificare il file `.magento.app.yaml` e rimuovere la Blackfire dalla sezione runtime:

   ```YAML
   ...
   # Enable extensions required by Magento 2
   runtime:
     extensions:
     - redis
     - xsl
     - json
     -**blackfire**
      - imap
   ...
   ```

1. Completa l’operazione nell’ambiente di sviluppo locale e passa al cloud.

Solo [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) se dopo l&#39;esecuzione di una distribuzione viene visualizzato il seguente errore:

*Avviso PHP: avvio PHP: impossibile caricare la libreria dinamica &#39;blackfire.so&#39; (tentativo: /usr/lib/php/20180731-zts/blackfire.so (/usr/lib/php/20180731-zts/blackfire.so: impossibile aprire il file di oggetti condivisi: nessun file o directory di questo tipo), /usr/lib/php/20180731-zts/blackfire.so.so (/usr/lib/php/20180731-zts/blackfire.so.so: impossibile aprire il file di oggetti condivisi: nessun file o directory di questo tipo)) in Sconosciuto alla riga 0*

Questo errore indica che è necessario aggiornare il plug-in Blackfire e interromperne il caricamento.

**Se si desidera utilizzare New Relic Infrastructure**:

Per informazioni su come accedere a New Relic Infrastructure, vedere [Accedere a New Relic](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html) nella Knowledge Base di supporto.
