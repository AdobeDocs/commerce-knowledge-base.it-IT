---
title: Ottenere e applicare [!UICONTROL security patch]
description: Questo articolo fornisce istruzioni su come ottenere e applicare un [!UICONTROL security patch] rilasciato, ma le istruzioni non sono disponibili.
exl-id: 55f2be73-2ccc-4750-a7bd-3058fc2d5107
source-git-commit: 06bc239cb5b1a894d2a60236a9b32b2b0c4eba80
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# Come ottenere e applicare un [!UICONTROL security patch]

Questo articolo fornisce istruzioni su come ottenere e applicare un [!UICONTROL security patch] rilasciato, ma le istruzioni non sono disponibili.

## Prodotti e versioni interessati

Adobe Commerce On-Premise e Cloud - Tutte le versioni

## Causa

La maggior parte di [!UICONTROL Security Patches] viene rilasciata senza alcun file fisico o hotfix da applicare.

## Soluzione


### Caso I:

Se nelle Note sulla versione è menzionato un file di patch fisico o un hotfix:

* Scarica il file dalla sezione di download di [https://account.magento.com](https://account.magento.com/downloads/view/). (Gli utenti con accesso condiviso devono prima ricevere i privilegi di download dal proprietario dell’account/titolare della licenza)

**Avvertenze:**

Se utilizzi una versione precedente di Adobe Commerce (2.4.4), avrai ricevuto automaticamente il supporto esteso. La versione deve essere una delle seguenti versioni non supportate per poter applicare le ultime patch di sicurezza disponibili:

2.4.4 - 2.4.4-p11

Le versioni non supportate (2.3.x, 2.4.0 - 2.4.3) non sono idonee per il supporto e devi prima eseguire l’aggiornamento a una versione supportata per sfruttare le ultime correzioni di sicurezza.

Se non si dispone del supporto esteso, è possibile richiedere il supporto per condividere le patch con l&#39;utente, ma non saranno in grado di risolvere eventuali problemi/errori riscontrati durante l&#39;applicazione.

### Caso II:

Se nelle Note sulla versione non è menzionato un file di patch fisico o un hotfix:

* **Cloud:**

1. Alcuni [!UICONTROL Security Patches] potrebbero essere inclusi/rilasciati nell&#39;ultima versione di Cloud Tools Suite (ECE Tools) in Cloud Patches for Commerce. Controllare le [Note sulla versione](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite) e, se nella versione è menzionata una correzione di sicurezza, aggiornare il pacchetto a tale versione.
1. Se le Note sulla versione non menzionano una correzione di sicurezza, continua a leggere.

* **Cloud o on-premise:**

* Se non è disponibile un file/hotfix di patch fisica, [aggiorna la versione di Adobe Commerce su Cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) 2.4.X all&#39;ultima versione della patch 2.4.X-pY.
* Se non è disponibile un file/hotfix di patch fisica, [aggiorna la versione di Adobe Commerce On-Premise](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade) 2.4.X all&#39;ultima versione della patch 2.4.X-pY.

## Lettura correlata

* Consulta le [note sulla versione della suite di strumenti Commerce Cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite) nella *Guida di Adobe Commerce sull&#39;infrastruttura cloud*.
* Consulta [Aggiornare Adobe Commerce versione](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) nella *Guida di Adobe Commerce sull&#39;infrastruttura cloud*.
