---
title: Ottenere e applicare [!UICONTROL security patch]
description: Questo articolo fornisce istruzioni su come ottenere e applicare un [!UICONTROL security patch] rilasciato, ma le istruzioni non sono disponibili.
exl-id: 55f2be73-2ccc-4750-a7bd-3058fc2d5107
source-git-commit: 43c8308c6539c53f60fb6457047898a2edd46532
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# Come ottenere e applicare un [!UICONTROL security patch]

>[!NOTE]
>Se si dispone di un&#39;installazione on-premise e non si utilizzano sistemi di controllo della versione come [!DNL CVS] o [!DNL GitHub] per gestire il codice, l&#39;host Web potrebbe essere in grado di fornire assistenza nell&#39;applicazione della patch. Puoi contattarli per ricevere supporto

Questo articolo fornisce istruzioni su come ottenere e applicare un [!UICONTROL security patch] rilasciato, ma le istruzioni non sono disponibili.

## Prodotti e versioni interessati

Adobe Commerce On-Premise e Cloud - Tutte le versioni


## Causa

La maggior parte di [!UICONTROL Security Patches] viene rilasciata senza patch o hotfix isolati da applicare e richiederà l&#39;aggiornamento alla versione [!UICONTROL Security Patch].

## Soluzione


### Caso I:

* Se nelle [Note sulla versione](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/release-notes/cloud-tools-suite) è menzionato un file/hotfix di patch isolato, scarica il file dalla sezione di download di [https://account.magento.com](https://account.magento.com/downloads/view/). Agli utenti con accesso condiviso devono prima essere concessi i privilegi di download dal proprietario dell’account/titolare della licenza.

**Avvertenze:**

Se utilizzi una versione precedente di Adobe Commerce (2.4.4), avrai ricevuto automaticamente il supporto esteso. La versione deve essere una delle seguenti versioni non supportate per poter applicare le ultime patch di sicurezza disponibili:

2.4.4 - 2.4.4-p11

Le versioni non supportate (2.3.x, 2.4.0 - 2.4.3) non sono idonee per il supporto e devi prima eseguire l’aggiornamento a una versione supportata per sfruttare le ultime correzioni di sicurezza.

Se non si dispone del supporto esteso, è possibile richiedere il supporto per condividere le patch con l&#39;utente, ma non saranno in grado di risolvere eventuali problemi/errori riscontrati durante l&#39;applicazione.

### Caso II:

Le patch isolate vengono fornite solo in casi eccezionali e non rappresentano la forma preferita per l&#39;implementazione di correzioni di sicurezza.

Se nelle Note sulla versione non è menzionato un file patch o un hotfix isolato:

* **Cloud:**

1. Alcuni [!UICONTROL Security Patches] potrebbero essere inclusi/rilasciati nell&#39;ultima versione di Cloud Tools Suite (ECE Tools) in Cloud Patches for Commerce. Controllare le [Note sulla versione](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite) e, se nella versione è menzionata una correzione di sicurezza, aggiornare il pacchetto a tale versione.
1. Se le Note sulla versione non menzionano una correzione di sicurezza, continua a leggere.

* **Cloud o on-premise:**

* Se un file/hotfix di patch isolato non è disponibile, [aggiorna la versione di Adobe Commerce su Cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) 2.4.X all&#39;ultima versione della patch 2.4.X-pY.
* Se un file/hotfix di patch isolato non è disponibile, [aggiorna la versione di Adobe Commerce On-Premise](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade) 2.4.X all&#39;ultima versione della patch 2.4.X-pY.

## Lettura correlata

* Consulta le [note sulla versione della suite di strumenti Commerce Cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite) nella *Guida di Adobe Commerce sull&#39;infrastruttura cloud*.
* Consulta [Aggiornare Adobe Commerce versione](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) nella *Guida di Adobe Commerce sull&#39;infrastruttura cloud*.
