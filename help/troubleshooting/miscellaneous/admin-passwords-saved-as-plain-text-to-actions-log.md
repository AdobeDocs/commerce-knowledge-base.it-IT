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

Questo articolo corregge la creazione di un nuovo utente con privilegi di amministratore da parte di un amministratore di Commerce e il salvataggio della password come testo normale nella tabella del database `magento_logging_event_changes`.

Per risolvere questo problema di sicurezza, installa Adobe Commerce 2.0.16 e 2.1.9 Security Update. Dopo aver applicato l&#39;aggiornamento della protezione, le password vengono crittografate e non vengono visualizzate come testo normale.

## Versioni interessate {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Affectedversions}

* Adobe Commerce on-premise 2.X.X
* Adobe Commerce sull’infrastruttura cloud 2.X.X

## Problema {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Issue}

Quando un amministratore Commerce esistente crea un nuovo utente con privilegi di amministratore tramite **Sistema** > **Autorizzazioni** > **Tutti gli utenti** > **Aggiungi nuovo utente**, la password (immessa come conferma) viene salvata come testo normale nella tabella del database `magento_logging_event_changes`.

### Passaggi da riprodurre: {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Stepstoreproduce}

1. Accedi come amministratore e crea un nuovo utente passando a questo percorso: **Sistema** > Autorizzazioni > **Tutti gli utenti**.

   ![add_user_magento_2.4.1.png](assets/add_user_magento_2.4.1.png)

1. Fare quindi clic sulla pagina **Aggiungi nuovo utente**. Fornisci la password dell&#39;amministratore corrente quando richiesto.
1. Vai alla pagina **Sistema** > **Registro azioni** > **Rapporto** e trova l&#39;ultima voce di registro.
1. La password corrente è visibile, senza crittografia né hash.

## Soluzione {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Solution}

Il problema è stato risolto installando [Adobe Commerce 2.0.16 e 2.1.9 Security Update](https://magento.com/security/patches/magento-2016-and-219-security-update).

Dopo aver installato l&#39;aggiornamento della sicurezza, la password viene crittografata e non viene visualizzata in testo normale nella tabella `magento_logging_event_changes`.

## Ulteriori informazioni {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Moreinformation}

[Adobe Commerce 2.0.16 e 2.1.9 Pagina di aggiornamento sulla sicurezza](https://magento.com/security/patches/magento-2016-and-219-security-update) nel nostro centro sicurezza.

[Aggiorna l&#39;applicazione Adobe Commerce e i relativi componenti](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/overview.html) nella documentazione per gli sviluppatori.
