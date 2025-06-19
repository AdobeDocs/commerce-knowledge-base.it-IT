---
title: Le richieste AJAX con throughput elevato causano prestazioni insoddisfacenti
description: Questo articolo fornisce una soluzione per i problemi di prestazioni con Adobe Commerce on-premise o Adobe Commerce sui siti dell’infrastruttura cloud a causa di alcune richieste di throughput elevate che causano un carico e un traffico significativi del server.
exl-id: 68dfca8a-826c-4476-acaf-a139052b5dcc
feature: Cache
role: Developer
source-git-commit: b6e44e106dcc546949459a79c0f2e49b87e1d376
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# Le richieste AJAX con throughput elevato causano prestazioni insoddisfacenti

Questo articolo fornisce una soluzione per i problemi di prestazioni con Adobe Commerce on-premise o Adobe Commerce sui siti dell’infrastruttura cloud a causa di alcune richieste di throughput elevate che causano un carico e un traffico significativi del server.

## Prodotti e versioni interessati

* Adobe Commerce sull’infrastruttura cloud 2.2.x, 2.3.x
* Adobe Commerce on-premise 2.2.x, 2.3.x

>[!NOTE]
>
>Il problema è stato risolto nella versione 2.3.4 sia di Adobe Commerce sull’infrastruttura cloud che di Adobe Commerce on-premise.

### Problema

Le prestazioni del sito sono lente a causa di richieste di throughput elevato, come le richieste critiche di AJAX.

### Causa

Le richieste di AJAX con throughput elevato includono quelle relative ai contenuti privati dei clienti.

### Soluzione

Sono disponibili tre soluzioni:

* [Eseguire l&#39;aggiornamento alla versione 2.3.4](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version).
* Assicurati richieste più leggere (memorizza nella cache le richieste o passa al contenuto privato dei clienti).
* Riduci il numero di richieste.

<u>Garantire richieste più leggere (memorizzare in cache le richieste o passare al contenuto privato dei clienti)</u>

Se in ogni pagina sono presenti richieste di AJAX di terze parti attivate, prova a memorizzarle nella cache o a spostarle nel contenuto privato dei clienti. Il commerciante può eseguire questa operazione assicurandosi che le richieste AJAX personalizzate vengano chiamate utilizzando i metodi HTTP GET. Renderà queste richieste memorizzabili nella cache da Fastly. Se ci sono richieste AJAX personalizzate che non devono essere memorizzate in cache, è necessario eseguirne il refactoring in base alla funzionalità di contenuto privato. Per i passaggi, consulta [Contenuto privato](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) nella documentazione per gli sviluppatori.

<u>Riduci il numero di richieste</u>

* Disattiva il carrello acquisti permanente, in quanto può aumentare il numero di `customer/section/load` richieste. Segui i passaggi descritti in [Percorsi persistenti del carrello](https://experienceleague.adobe.com/it/docs/commerce-operations/configuration-guide/paths/config-reference-general) nella documentazione per gli sviluppatori per verificare se il carrello permanente è abilitato.
* Se devi ricaricare o annullare la validità del contenuto in `sections.xml`, segui i passaggi descritti in [Contenuto privato: annulla la validità del contenuto privato](https://developer.adobe.com/commerce/php/development/cache/page/private-content/#invalidate-private-content) nella documentazione per sviluppatori. Assicurarsi di non utilizzare il metodo `customerData.reload()` direttamente nelle personalizzazioni.
* Controlla altre richieste POST AJAX sulla stessa pagina. Apri Google Chrome Developer Tool nel browser Google Chrome. Fare clic sulla scheda **Rete** e quindi sulla scheda **XHR**. Verrà visualizzato l&#39;elenco di tutte le richieste di AJAX dalla pagina specifica. Fai clic su ogni richiesta e nel campo Request Method (Metodo di richiesta) dovresti trovare le richieste di GET. Nota: Google Chrome viene utilizzato come esempio ed è possibile farlo anche in altri browser.
* Verifica la funzionalità Google Tag Manager (GTM) che è una richiesta AJAX specifica. L’utente può rimuovere questo AJAX e rieseguire il factoring della loro personalizzazione con funzionalità private per ridurre il numero totale di richieste al server.
* Controlla se il banner di Adobe Commerce è abilitato ma non utilizzato. Potrebbe essere necessario [Disattivare l&#39;output del banner Adobe Commerce per migliorare le prestazioni del sito](https://experienceleague.adobe.com/it/docs/experience-cloud-kcs/kbarticles/ka-26909).

### Lettura correlata

Per ulteriori informazioni sui contenuti privati dei clienti, consulta [Contenuto privato](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) nella documentazione per gli sviluppatori.
