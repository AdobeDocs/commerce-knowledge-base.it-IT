---
title: Password amministratore salvate come testo normale nel registro delle azioni
description: Questo articolo fornisce una correzione per quando un amministratore di Commerce crea un nuovo utente con i privilegi di amministratore e la password viene salvata come testo normale nella tabella di database "magento_logging_event_changes".
exl-id: 0e91198e-66b9-456a-9b75-5986369ed8e6
feature: Admin Workspace, Logs
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# Password amministratore salvate come testo normale nel registro delle azioni

Questo articolo corregge i casi in cui un amministratore di Commerce crea un nuovo utente con i privilegi di amministratore e la password viene salvata come testo normale in `magento_logging_event_changes` tabella di database.

Per risolvere questo problema di sicurezza, installa Adobe Commerce 2.0.16 e 2.1.9 Security Update. Dopo aver applicato l&#39;aggiornamento della protezione, le password vengono crittografate e non vengono visualizzate come testo normale.

## Versioni interessate {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Affectedversions}

* Adobe Commerce on-premise 2.X.X
* Adobe Commerce sull’infrastruttura cloud 2.X.X

## Problema {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Issue}

Quando un amministratore Commerce esistente crea un nuovo utente con i privilegi di amministratore tramite **Sistema** > **Autorizzazioni** > **Tutti gli utenti** > **Aggiungi nuovo utente**, la password (immessa come conferma) viene salvata come testo normale nel `magento_logging_event_changes` tabella di database.

### Passaggi da riprodurre: {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Stepstoreproduce}

1. Accedi come amministratore e crea un nuovo utente passando a questo percorso: **Sistema** > Autorizzazioni > **Tutti gli utenti**.

   ![add_user_magento_2.4.1.png](assets/add_user_magento_2.4.1.png)

1. Quindi fai clic su **Aggiungi nuovo utente** pagina. Fornisci la password dell&#39;amministratore corrente quando richiesto.
1. Vai a **Sistema** > **Registro azioni** > **Report** e trovare l&#39;ultima voce di registro.
1. La password corrente è visibile, senza crittografia né hash.

## Soluzione {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Solution}

Installazione di [Aggiornamento sulla sicurezza di Adobe Commerce 2.0.16 e 2.1.9](https://magento.com/security/patches/magento-2016-and-219-security-update) risolve questo problema.

Dopo aver installato l’aggiornamento della sicurezza, la password viene crittografata e non viene visualizzata in testo normale in `magento_logging_event_changes` tabella.

## Ulteriori informazioni {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Moreinformation}

[Pagina di aggiornamento sulla sicurezza di Adobe Commerce 2.0.16 e 2.1.9](https://magento.com/security/patches/magento-2016-and-219-security-update) nel nostro centro di sicurezza.

[Aggiornare l’applicazione e i componenti di Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/overview.html) nella documentazione per gli sviluppatori.
