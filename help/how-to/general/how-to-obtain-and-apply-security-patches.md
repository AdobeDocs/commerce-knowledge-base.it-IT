---
title: Ottenere e applicare [!UICONTROL security patch]
description: Questo articolo fornisce istruzioni su come ottenere e applicare un [!UICONTROL security patch] rilasciato, ma le istruzioni non sono disponibili.
exl-id: 55f2be73-2ccc-4750-a7bd-3058fc2d5107
source-git-commit: b15a1d008b6cc2bdce797768e6ee7029a747e6da
workflow-type: tm+mt
source-wordcount: '332'
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

Se utilizzi una versione precedente di Adobe Commerce e hai acquistato il supporto esteso, la tua versione deve essere una delle seguenti per poter applicare le patch di sicurezza:

* 2.4.2-p2
* 2.4.3-p3

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

* Consulta le [note sulla versione per la suite di strumenti Commerce Cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite) nella *Guida di Adobe Commerce sull&#39;infrastruttura cloud*.
* Consulta [Aggiornare Adobe Commerce versione](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) nella *Guida di Adobe Commerce sull&#39;infrastruttura cloud*.
