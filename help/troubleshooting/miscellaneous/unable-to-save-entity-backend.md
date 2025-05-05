---
title: Impossibile salvare il backend Adobe Commerce dell’entità
description: Questo articolo fornisce una soluzione per i casi in cui non è possibile salvare un’entità nel backend di Adobe Commerce. Ad esempio, quando non puoi modificare e salvare una regola "cart_price" specifica.
exl-id: e45dc88a-2da0-4524-bd61-6634cfebb169
feature: Admin Workspace, Marketing Tools
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# Impossibile salvare il backend Adobe Commerce dell’entità

Questo articolo fornisce una soluzione per i casi in cui non è possibile salvare un’entità nel backend di Adobe Commerce. Ad esempio, quando non è possibile modificare e salvare una regola `cart_price` specifica.

## Prodotti e versioni interessati

Questo problema può interessare tutte le versioni di Adobe Commerce in cui è configurata la dimensione massima della sessione. È stato aggiunto a partire dal Magento Open Source 2.3.7-p1 e da Adobe commerce (tutti i metodi di distribuzione) 2.4.3.


## Problema

Quando tenti di riconfigurare lo store, la pagina viene ricaricata e le modifiche non vengono salvate. È possibile visualizzare un messaggio in `var/log/system.log`:

Rapporto *[2021-11-27 00:30:52].AVVISO: la dimensione della sessione di 418056 ha superato la dimensione massima di 256000 consentita per la sessione. [][]*

<u>Passaggi da riprodurre</u>:

Esempio di configurazione dell’archivio non salvata:

1. Seleziona una regola nell&#39;archivio Adobe Commerce in Produzione > **Marketing** > **Regole prezzo carrello**.
1. Scegliere una regola e impostarla su *Inattiva* e salvare la modifica.

<u>Risultato previsto</u>:

La regola è impostata su inattiva.

<u>Risultato effettivo</u>:

* La pagina viene ricaricata senza alcun messaggio.
* La regola è ancora impostata su attiva.

## Causa

Questo problema è relativo alle nuove funzionalità introdotte di recente che hanno interessato la dimensione massima della sessione. Consulta [Gestione delle sessioni](https://experienceleague.adobe.com/it/docs/commerce-admin/systems/security/security-session-management) nella documentazione per gli sviluppatori.

## Soluzione

Aumentare il valore &quot;Dimensione massima sessione&quot; in (**Archivi** > **Configurazione** > **Avanzate** > **Sistema** > **Sicurezza** > Dimensione massima sessione).

## Lettura correlata

* [Menu Marketing](https://experienceleague.adobe.com/it/docs/commerce-admin/marketing/marketing-menu) nella guida utente.
