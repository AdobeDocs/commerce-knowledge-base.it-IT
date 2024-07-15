---
title: Impossibile accedere all’ultima versione non definitiva di Adobe Commerce
description: Questo articolo fornisce soluzioni per i problemi che si verificano quando si tenta di utilizzare il codice pre-release più recente di Adobe Commerce.
exl-id: cbf54a15-b307-4bfc-90b7-cff98aeb4fce
feature: Roles/Permissions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 0%

---

# Impossibile accedere all’ultima versione non definitiva di Adobe Commerce

Questo articolo fornisce soluzioni per i problemi che si verificano quando si tenta di utilizzare il codice pre-release più recente di Adobe Commerce.

>[!NOTE]
>
>In caso di problemi con l&#39;accesso a Beta, fare riferimento all&#39;articolo [Impossibile accedere alla versione più recente di Beta](/help/how-to/general/cannot-access-the-latest-beta-version.md).

## Problema

Questo articolo tratta i seguenti problemi relativi all’accesso al codice pre-release:

* Non è possibile individuare il codice di pre-release.
* Impossibile scaricare la versione ad accesso anticipato di Adobe Commerce da [magento.com](https://account.magento.com/customer/account/login) tramite Composer.

## Causa

Queste sono le cause più comuni dei problemi:

* Stai cercando il codice di accesso anticipato nella posizione sbagliata.
* Stai utilizzando l’ID immagine errato quando accedi al codice tramite Composer.
* Il tuo account non fa parte del programma di pre-release.

## Soluzione

### Posizione codice di accesso anticipato

Durante la fase di pre-release, i pacchetti di rilascio sono disponibili in due posizioni:

1. Tramite Composer su [magento.com](https://repo.magento.com/) utilizzando l&#39;ID immagine principale per l&#39;account. Per ulteriori dettagli su come utilizzare Composer, consulta [Installare Adobe Commerce utilizzando Composer](https://devdocs.magento.com/guides/v2.3/install-gde/composer.html) nella documentazione per gli sviluppatori.
1. **Il mio account** > **Download** su [account.magento.com](https://account.magento.com/customer/account/login).

>[!NOTE]
>
>I pacchetti di rilascio non sono disponibili su GitHub fino alla data GA.

### MageID da utilizzare

Devi utilizzare l’ID immagine principale associato al tuo account Adobe Commerce o Partner. Il programma preliminare non è collegato ad alcun contatto con accesso condiviso. È possibile accedere in anteprima solo tramite Composer o [repo.magento.com](https://repo.magento.com/) dal MageID associato alla licenza Adobe Commerce o alla licenza Partner.

#### Come posso sapere se il mio MageID è quello principale?

**Per i commercianti**

Per verificare se l&#39;ID immagine è primario, provare a eseguire le operazioni seguenti:

1. Accedi a [magento.com](https://account.magento.com/customer/account/login) e passa alla scheda **Prodotti e servizi**. Controlla se visualizzi le informazioni sulla licenza di Adobe Commerce:
   * Se trovi le informazioni sulla licenza di Adobe Commerce, il tuo MageID è primario.
   * Se non visualizzi le informazioni sulla licenza di Adobe Commerce, il tuo MageID dispone solo dell’accesso condiviso. Per scoprire chi è il titolare dell&#39;ID primario, vai a **Condiviso con me** Notare il SHARENAME ivi specificato. Fare clic su **Cambia account** e selezionare il valore indicato in SHARENAME. Nella pagina di benvenuto viene visualizzata l’e-mail del titolare dell’ID primario.
1. Se per qualsiasi motivo non riesci a trovare queste informazioni in [magento.com](https://account.magento.com/customer/account/login), contatta il tuo account team di Adobi.
1. Se non funziona nessuno di questi, [contatta l&#39;assistenza](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

**Per i partner**

Per verificare se l&#39;ID immagine è primario, provare a eseguire le operazioni seguenti:

1. Accedi a [magento.com](https://account.magento.com/customer/account/login) e passa alla scheda **Prodotti e servizi**. Nella sottosezione Partner verificare se sono presenti le informazioni sulla licenza del partner attivo:
   * Se vengono visualizzate le informazioni sulla licenza del partner attivo, il MageID è primario. La licenza Partner è attiva se il valore DATA FINE è una data futura.
   * Se non vengono visualizzate le informazioni sulla licenza del partner attivo, il tuo MageID ha solo accesso condiviso. Per scoprire chi è il titolare dell&#39;ID primario, vai a **Condiviso con me** Notare il SHARENAME ivi specificato. Fare clic su **Cambia account** e selezionare il valore indicato in SHARENAME. Nella pagina di benvenuto viene visualizzata l’e-mail del titolare dell’ID primario.
1. Se per qualsiasi motivo non riesci a trovare queste informazioni in [magento.com](https://account.magento.com/customer/account/login), contatta il tuo Partner Manager.
1. Se non funziona nessuno di questi, [сcontatta l&#39;assistenza](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Non fa parte del programma pre-release

Per essere inclusa nel programma di accesso pre-release, la tua organizzazione deve disporre di un account Adobe Commerce o Partner attivo e in buono stato. Se ritieni di soddisfare questi criteri e di non poter accedere al codice pre-release, [contatta l&#39;assistenza](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) con il tuo MageID.
