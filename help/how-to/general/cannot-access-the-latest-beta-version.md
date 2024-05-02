---
title: Impossibile accedere alla versione beta più recente
description: Questo articolo fornisce soluzioni ai problemi che si verificano quando si tenta di utilizzare le versioni beta più recenti del codice per Adobe Commerce. Il codice beta è disponibile solo per i partner ufficiali di Adobi che hanno seguito la procedura descritta in [Adobe Commerce Beta Program](https://github.com/magento/magento2/wiki/Magento-Beta-Program).
exl-id: a53c854e-38a8-4c8c-8586-9d99c576c835
source-git-commit: c1c2bd29e14f4cbfffb235801e95ec7cbb7c7a55
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# Impossibile accedere alla versione beta più recente

Questo articolo fornisce soluzioni ai problemi che si verificano quando si tenta di utilizzare le versioni beta più recenti del codice per Adobe Commerce. Il codice beta è disponibile solo per i partner Adobi ufficiali che hanno seguito la procedura descritta in [Programma Adobe Commerce Beta](https://github.com/magento/magento2/wiki/Magento-Beta-Program).

## Problema

Questo articolo tratta i seguenti problemi relativi all’accesso anticipato al codice di accesso:

* La versione beta di Adobe Commerce non è disponibile per il download in **Il mio account** > **Download** il [magento.com](https://account.magento.com/customer/account/login).
* Impossibile scaricare la versione ad accesso anticipato di Adobe Commerce da [magento.com](https://account.magento.com/customer/account/login) mediante Compositore.

## Causa

Queste sono le cause più comuni dei problemi:

* Stai cercando il codice di accesso anticipato nella posizione sbagliata.
* Stai utilizzando un MageID errato.
* Lo sviluppatore deve accedere alle chiavi dal MageID corretto.
* Il tuo account non fa parte del programma beta.

## Soluzione

### Posizione codice di accesso anticipato

Durante i periodi di accesso beta, i pacchetti di rilascio sono disponibili solo tramite Compositore su [repo.magento.com](https://repo.magento.com/). I pacchetti di rilascio non sono disponibili sui portali GitHub e Adobe Commerce in questo periodo e verranno pubblicati in queste posizioni nella data GA. Per ulteriori dettagli su come utilizzare Compositore, fai clic su [qui](https://devdocs.magento.com/guides/v2.3/install-gde/composer.html).

### MageID da utilizzare

Devi utilizzare il MageID principale associato al tuo account Partner. Il programma beta non è collegato ad alcun contatto con accesso condiviso. È possibile accedere in anteprima solo tramite Compositore o [repo.magento.com](https://repo.magento.com/) tramite il MageID associato alla licenza Partner.

#### Come posso sapere se il mio MageID è quello principale

Per verificare se l&#39;ID immagine è primario, provare a eseguire le operazioni seguenti:

1. Accedi a [magento.com](https://account.magento.com/customer/account/login) e vai al **I miei prodotti e servizi** scheda. Nella sottosezione Partner verificare se sono presenti le informazioni sulla licenza del partner attivo:
   * Se vengono visualizzate le informazioni sulla licenza del partner attivo, il MageID è primario. La licenza Partner è attiva se il valore DATA FINE è una data futura.
   * Se non vengono visualizzate le informazioni sulla licenza del partner attivo, il tuo MageID ha solo accesso condiviso. Per scoprire chi è il titolare dell&#39;ID primario, vai al **Condiviso con me** Osserva il SHARENAME specificato. Clic **Cambia account** e selezionare il valore indicato in SHARENAME. Nella pagina di benvenuto viene visualizzata l’e-mail del titolare dell’ID primario.
1. Se per qualsiasi motivo non riesci a trovare queste informazioni su [magento.com](https://account.magento.com/customer/account/login), contatta il tuo Partner Manager.
1. Se nessuna delle condizioni descritte funziona, si prega di [contatta l’assistenza](/help/help-center-guide/help-center/magento-help-center-user-guide.md#merchant-not-displayed).

#### Lo sviluppatore non dispone dell’accesso corretto alle chiavi

Se sei il proprietario MageID principale e devi concedere l’accesso a uno sviluppatore del tuo team, segui i passaggi seguenti:

1. Chiedi al proprietario dell’MageID principale di accedere [account.magento.com](https://account.magento.com/customer/account/login).
1. Seleziona la **Marketplace** e quindi fare clic su **Chiavi di accesso**.
1. Seleziona **Creare una nuova chiave di accesso** e denominalo.
1. Invia le chiavi al tuo sviluppatore.

### Non fa parte del programma di accesso anticipato

Il nostro programma di accesso beta è disponibile solo per i nostri partner tecnici e di soluzioni, in modo che possano valutare il nostro codice di pre-produzione. Per essere inclusa nel programma di accesso beta, la tua organizzazione deve disporre di un account Adobe Partner attivo che sia in buono stato e abbia firmato la Beta NDA [qui](https://github.com/magento/magento2/wiki/Magento-Beta-Program). Se ritieni di soddisfare questi criteri e non riesci ad accedere al codice beta, contatta [commercebeta@adobe.com](mailto:commercebeta@adobe.com).
