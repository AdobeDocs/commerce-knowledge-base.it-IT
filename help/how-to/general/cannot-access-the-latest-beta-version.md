---
title: Impossibile accedere alla versione più recente di Beta
description: Questo articolo fornisce soluzioni ai problemi che si verificano quando si tenta di utilizzare le versioni più recenti del codice Beta per Adobe Commerce. Il codice Beta è disponibile solo per i partner Adobe ufficiali che hanno seguito il processo descritto in [Programma Adobe Commerce Beta](https://github.com/magento/magento2/wiki/Magento-Beta-Program).
exl-id: a53c854e-38a8-4c8c-8586-9d99c576c835
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# Impossibile accedere alla versione più recente di Beta

Questo articolo fornisce soluzioni ai problemi che si verificano quando si tenta di utilizzare le versioni più recenti del codice Beta per Adobe Commerce. Il codice Beta è disponibile solo per i partner ufficiali di Adobe che hanno seguito la procedura descritta in [Programma Adobe Commerce Beta](https://github.com/magento/magento2/wiki/Magento-Beta-Program).

## Problema

Questo articolo tratta i seguenti problemi relativi all’accesso anticipato al codice di accesso:

* La versione di Adobe Commerce Beta non è disponibile per il download in **Il mio account** > **Download** in [magento.com](https://account.magento.com/customer/account/login).
* Impossibile scaricare la versione ad accesso anticipato di Adobe Commerce da [magento.com](https://account.magento.com/customer/account/login) tramite Composer.

## Causa

Queste sono le cause più comuni dei problemi:

* Stai cercando il codice di accesso anticipato nella posizione sbagliata.
* Stai utilizzando un MageID errato.
* Lo sviluppatore deve accedere alle chiavi dal MageID corretto.
* Il tuo account non fa parte del programma Beta.

## Soluzione

### Posizione codice di accesso anticipato

Durante i periodi di accesso beta, i pacchetti di rilascio sono disponibili solo tramite Composer su [repo.magento.com](https://repo.magento.com/). I pacchetti di rilascio non sono disponibili sui portali GitHub e Adobe Commerce in questo periodo e verranno pubblicati in queste posizioni nella data GA. Per ulteriori dettagli su come utilizzare Composer, fare clic [qui](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/composer).

### MageID da utilizzare

Devi utilizzare il MageID principale associato al tuo account Partner. Il programma Beta non è collegato ad alcun contatto con accesso condiviso. È possibile accedere in anteprima solo tramite Composer o [repo.magento.com](https://repo.magento.com/) dal MageID associato alla licenza Partner.

#### Come posso sapere se il mio MageID è quello principale

Per verificare se l&#39;ID immagine è primario, provare a eseguire le operazioni seguenti:

1. Accedi a [magento.com](https://account.magento.com/customer/account/login) e passa alla scheda **Prodotti e servizi**. Nella sottosezione Partner verificare se sono presenti le informazioni sulla licenza del partner attivo:
   * Se vengono visualizzate le informazioni sulla licenza del partner attivo, il MageID è primario. La licenza Partner è attiva se il valore DATA FINE è una data futura.
   * Se non vengono visualizzate le informazioni sulla licenza del partner attivo, il tuo MageID ha solo accesso condiviso. Per scoprire chi è il titolare dell&#39;ID primario, vai a **Condiviso con me** Notare il SHARENAME ivi specificato. Fare clic su **Cambia account** e selezionare il valore indicato in SHARENAME. Nella pagina di benvenuto viene visualizzata l’e-mail del titolare dell’ID primario.
1. Se per qualsiasi motivo non riesci a trovare queste informazioni in [magento.com](https://account.magento.com/customer/account/login), contatta il tuo Partner Manager.
1. Se non funziona nessuno di questi, [contatta l&#39;assistenza](/help/help-center-guide/help-center/magento-help-center-user-guide.md#merchant-not-displayed).

#### Lo sviluppatore non dispone dell’accesso corretto alle chiavi

Se sei il proprietario MageID principale e devi concedere l’accesso a uno sviluppatore del tuo team, segui i passaggi seguenti:

1. Accedi a [account.magento.com](https://account.magento.com/customer/account/login) come proprietario MageID primario.
1. Selezionare la scheda **Marketplace**, quindi fare clic su **Chiavi di accesso**.
1. Selezionare **Crea una nuova chiave di accesso** e denominarla.
1. Invia le chiavi al tuo sviluppatore.

### Non fa parte del programma di accesso anticipato

Il nostro programma Beta Access è disponibile solo per i nostri partner tecnici e di soluzioni, in modo che possano valutare il nostro codice di preproduzione. Per essere inclusa nel programma Beta Access, la tua organizzazione deve disporre di un account partner Adobe attivo che sia in buono stato e abbia firmato il NDA di Beta [qui](https://github.com/magento/magento2/wiki/Magento-Beta-Program). Se ritieni di soddisfare questi criteri e di non poter accedere al codice beta, contatta [commercebeta@adobe.com](mailto:commercebeta@adobe.com).
