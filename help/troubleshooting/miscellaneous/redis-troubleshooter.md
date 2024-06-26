---
title: Risoluzione dei problemi Redis su Adobe Commerce
description: Questo articolo è uno strumento di risoluzione dei problemi per Adobe Commerce on-premise e Adobe Commerce sui commercianti di infrastrutture cloud che hanno problemi con Redis. Fare clic su ogni domanda per visualizzare la risposta in ogni passaggio della risoluzione dei problemi. A seconda dei sintomi e della configurazione, lo strumento di risoluzione dei problemi spiegherà come risolvere i problemi di versione e memoria e ottimizzare le prestazioni.
exl-id: 241abcfd-33b8-449b-b385-32950bd26320
feature: Services, Support
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '566'
ht-degree: 0%

---

# Risoluzione dei problemi Redis su Adobe Commerce

Questo articolo è uno strumento di risoluzione dei problemi per Adobe Commerce on-premise e Adobe Commerce sui commercianti di infrastrutture cloud che hanno problemi con Redis. Fare clic su ogni domanda per visualizzare la risposta in ogni passaggio della risoluzione dei problemi. A seconda dei sintomi, lo strumento di risoluzione dei problemi spiegherà come risolvere i problemi di versione e memoria e ottimizzare le prestazioni.

## Passaggio 1 - Problema Redis {#step-1}

+++Problema Redis?

a. SÌ - Procedere come segue [Passaggio 2](#step2)</a>.

b. NO - Torna a [support.magento.com](https://support.magento.com/hc/en-us) e cercare gli articoli pertinenti per la risoluzione dei problemi.

+++

## Passaggio 2 - Conferma patch Redis installate {#step-2}

+++Le patch Redis correnti sono installate?

a. SÌ - Procedere come segue [Passaggio 3](#step3)</a>.

b. NO - Assicurati di disporre della versione più recente del pacchetto `magento-cloud-patches` installato. Questo pacchetto contiene le patch necessarie per Redis. Per accedere, vai a [Patch magneto-cloud GitHub](https://github.com/magento/magento-cloud-patches/).

+++

## Passaggio 3 - Supporto della versione Redis {#step-3}

+++Su Redis versioni 3.2 o 5.0?

Controllare eseguendo i seguenti comandi nella CLI. Pro o staging: `$ redis-cli -p %port-number% info | grep redis_version`, dove `%port-number%` è il numero della porta, che si trova nel `app/etc/env.php` o eseguendo uno dei seguenti comandi: `$ vendor/bin/ece-tools env:config:show | grep -i redis -A 3` o `$ cat app/etc/env.php | grep redis -A 3` Starter o integrazione: `$ redis-cli -h 'redis.internal' info | grep redis_version`

a. SÌ - Procedere come segue [Passaggio 4](#step4).

b. NO - Adobe Commerce supporta Redis versioni 3.2 e 5.0. Se utilizzi Adobe Commerce su infrastruttura cloud 2.3.3 o versione successiva, ti consigliamo di effettuare l’aggiornamento a Redis 5. Per le fasi di configurazione di Adobe Commerce sull&#39;infrastruttura cloud Architettura del piano Pro, Integrazione e ambienti Starter, incluso il ramo principale, fare riferimento a [Adobe Commerce sull’infrastruttura cloud > Configurazione del servizio Redis](https://devdocs.magento.com/cloud/project/services-redis.html)</a> nella documentazione per gli sviluppatori. **Devi [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) per modificare la configurazione del servizio negli ambienti di produzione e staging dell&#39;architettura Pro. Inoltre, per Adobe Commerce su infrastruttura cloud e Adobe Commerce on-premise 2.3.5+, si consiglia l’implementazione della cache Redis estesa. Questo tipo di implementazione della cache di Redis offre miglioramenti che riducono al minimo il numero di query a Redis eseguite su ogni richiesta di Adobe Commerce. Per i passaggi, consulta [Implementazione della cache Redis estesa con Adobe Commerce 2.3.5+](https://support.magento.com/hc/en-us/articles/360049292532) nella nostra knowledge base di supporto. Per tutti gli altri utenti di Adobe Commerce, consulta [Guida alla configurazione di Adobe Commerce > Configura Redis](https://devdocs.magento.com/guides/v2.4/config-guide/redis/config-redis.html) nella documentazione per gli sviluppatori, per i passaggi.

+++

## Passaggio 4 - Verificare la versione più recente di ECE-Tools {#step-4}

+++Disponi della versione più recente di [Strumenti ECE > v2002.1.1](https://github.com/magento/ece-tools/releases)?

Verificare la versione disponibile eseguendo il comando in CLI/Terminal: `$php vendor/bin/composer info magento/ece-tools`.

a. SÌ - Procedere come segue [Passaggio 5](#step5).

b. N. - [Aggiornamento di ECE-Tools](https://devdocs.magento.com/cloud/project/ece-tools-update.html) alla versione più recente.

+++

## Passaggio 5: valutare il traffico di rete {#step-5}

+++L’app e Redis sono soggette a molto traffico di rete?

a. SÌ - Provare quanto segue: per un&#39;architettura non divisa, assicurarsi che [connessione secondaria](/help/troubleshooting/database/mysql-high-load-bottleneck-in-magento-commerce-cloud.md) viene utilizzato. Per l&#39;architettura divisa, [La cache L2 deve essere abilitata](https://devdocs.magento.com/guides/v2.4/config-guide/cache/two-level-cache.html).

b. NO - Configurare la configurazione della cache L2 tramite [Aggiornamento back-end Redis](https://devdocs.magento.com/cloud/env/variables-deploy.html#redis_backend). Procedi a [Passaggio 6](#step6).

+++

## Passaggio 6 - Controllare la velocità del sito {#step-6}

+++Il sito funziona ancora lentamente dopo l’abilitazione della cache L2?

a. YES - Controllare la directory temp `/dev/shm` per verificare se è necessario aumentare lo spazio. Se hai bisogno di più spazio, [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
b. NO - L’abilitazione della cache L2 sembra aver risolto i problemi Redis.

+++

[Torna al passaggio 1](#step-1)
