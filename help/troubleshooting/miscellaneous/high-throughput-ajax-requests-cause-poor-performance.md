---
title: Le richieste AJAX a throughput elevato causano prestazioni insoddisfacenti
description: Questo articolo fornisce una soluzione per i problemi di prestazioni con Adobe Commerce on-premise o Adobe Commerce sui siti dell’infrastruttura cloud a causa di alcune richieste di throughput elevate che causano un carico e un traffico significativi del server.
exl-id: 68dfca8a-826c-4476-acaf-a139052b5dcc
feature: Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# Le richieste AJAX a throughput elevato causano prestazioni insoddisfacenti

Questo articolo fornisce una soluzione per i problemi di prestazioni con Adobe Commerce on-premise o Adobe Commerce sui siti dell’infrastruttura cloud a causa di alcune richieste di throughput elevate che causano un carico e un traffico significativi del server.

## Prodotti e versioni interessati

* Adobe Commerce sull’infrastruttura cloud 2.2.x, 2.3.x
* Adobe Commerce on-premise 2.2.x, 2.3.x

>[!NOTE]
>
>Il problema è stato risolto nella versione 2.3.4 sia di Adobe Commerce sull’infrastruttura cloud che di Adobe Commerce on-premise.

### Problema

Il sito presenta un rallentamento delle prestazioni a causa di richieste di throughput elevato, come le richieste AJAX critiche.

### Causa

Le richieste AJAX a throughput elevato includono quelle relative ai contenuti privati dei clienti.

### Soluzione

Sono disponibili tre soluzioni:

* [Aggiornamento alla versione 2.3.4](https://devdocs.magento.com/cloud/project/project-upgrade.html). Se attualmente ciò non è possibile, [installare la patch per risolvere il problema](/help/troubleshooting/known-issues-patches-attached/performance-issues-caused-by-excessive-ajax-requests.md).
* Assicurati richieste più leggere (memorizza nella cache le richieste o passa al contenuto privato dei clienti).
* Riduci il numero di richieste.

<u>Garantire richieste più leggere (memorizza nella cache le richieste o passa al contenuto privato dei clienti)</u>

Se in ogni pagina sono presenti richieste AJAX di terze parti attivate, prova a memorizzarle nella cache o a spostarle nel contenuto privato dei clienti. Il commerciante può eseguire questa operazione assicurandosi che le richieste AJAX personalizzate vengano chiamate utilizzando i metodi HTTP GET. Renderà queste richieste memorizzabili nella cache da Fastly. Se ci sono richieste AJAX personalizzate che non devono essere memorizzate in cache, è necessario eseguirne il refactoring in base alla funzionalità di contenuto privato. Per i passaggi, consulta [Contenuto privato](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/cache/page-caching/private-content.html) nella documentazione per gli sviluppatori.

<u>Ridurre il numero di richieste</u>

* Disattiva il carrello persistente, in quanto può aumentare il numero di `customer/section/load` richieste. Segui i passaggi descritti in [Percorsi persistenti del carrello](https://devdocs.magento.com/guides/v2.3/config-guide/prod/config-reference-most.html#persistent-shopping-cart-paths) nella documentazione per sviluppatori per verificare se è abilitato il carrello acquisti persistente.
* Se devi ricaricare o annullare la validità del contenuto in `sections.xml` segui i passaggi descritti in [Contenuto privato: annullare la validità del contenuto privato](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/cache/page-caching/private-content.html#invalidate-private-content) nella documentazione per gli sviluppatori. Assicurati di non utilizzare il `customerData.reload()` direttamente nelle personalizzazioni.
* Controlla le altre richieste AJAX di POST sulla stessa pagina. Apri lo strumento per sviluppatori Google Chrome nel browser Google Chrome. Fai clic sul pulsante **Rete** e quindi la scheda **XHR** e sarà disponibile l’elenco di tutte le richieste AJAX dalla pagina specifica. Quindi fai clic su ciascuna richiesta e nel campo Request Method (Metodo di richiesta) dovrebbero essere le richieste GET. Nota: Google Chrome viene utilizzato come esempio ed è possibile farlo anche in altri browser.
* Verifica la funzionalità Google Tag Manager (GTM) che è una richiesta AJAX specifica. L’utente può rimuovere questo AJAX e rieseguire il factoring della personalizzazione con funzionalità private per ridurre il numero totale di richieste al server.
* Controlla se il banner di Adobe Commerce è abilitato ma non utilizzato. Potrebbe essere necessario [Disattiva l&#39;output del banner Adobe Commerce per migliorare le prestazioni del sito](/help/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.md).

### Lettura correlata

Per ulteriori informazioni sui contenuti per clienti privati, consulta [Contenuto privato](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/cache/page-caching/private-content.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=ajax%20requests) nella documentazione per gli sviluppatori.
