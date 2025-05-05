---
title: Come creare un’immagine "eliminata" quando richiesto dall’agente di supporto
description: Questo articolo fornisce informazioni su come creare un’immagine (backup) "pulita" del database e del codice da parte dell’amministratore di Adobe Commerce, quando richiesto da un agente di supporto Adobe Commerce. Questo dump esclude i file multimediali per accelerare il processo e ottenere un file molto più piccolo. Durante il backup del database viene eseguito l'hashing di tutti i dati sensibili.
exl-id: ad088bd2-3f92-416e-89f0-d037d53cd6a9
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---

# Come creare un’immagine &quot;eliminata&quot; quando richiesto dall’agente di supporto


## Prodotti e versioni interessati

Adobe Commerce (tutti i metodi di distribuzione) 2.3.x, 2.4.x.

## Creare un’immagine &quot;pulita&quot;

Crea un dump &quot;scrubbed&quot; dall’amministratore:

1. In Amministrazione Commerce, vai a **Sistema** > **Supporto** > **Agente di raccolta dati**.
1. Fare clic su **Nuovo backup**.
1. Dopo alcuni minuti, fare clic su **Aggiorna stato** (l&#39;operazione potrebbe richiedere più tempo, ripetere ogni 5 minuti fino al completamento).
1. Trasferire i file di dump generati dalla directory `/var/support` alla directory principale di Adobe Commerce.

Puoi quindi fornire a Supporto del collegamento di download diretto ai file di dump (il tuo indirizzo dello store e il nome del file come visualizzato).

In caso di problemi durante la creazione delle immagini da Admin, è consigliabile utilizzare i comandi CLI come descritto in [Eseguire le utilità di supporto](https://experienceleague.adobe.com/it/docs/commerce-operations/configuration-guide/cli/run-support-utilities) nella documentazione per gli sviluppatori.

## Lettura correlata

* [Crea un backup completo del database per Adobe Commerce sull&#39;infrastruttura cloud](/help/how-to/general/create-database-dump-on-cloud.md) nella knowledge base di supporto.
