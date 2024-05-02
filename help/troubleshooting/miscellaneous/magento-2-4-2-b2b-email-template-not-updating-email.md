---
title: "Adobe Commerce 2.4.2 B2B: il modello e-mail non aggiorna l’e-mail"
description: Questo articolo descrive un problema noto di Adobe Commerce 2.4.2 B2B in cui l’aggiornamento di alcune informazioni in un modello e-mail non viene aggiornato nelle e-mail. Questo problema influisce sui contenuti e-mail come informazioni sul cliente, tassi di valuta, simbolo di valuta, modifica del modello e-mail, ecc. Al momento non è disponibile una soluzione, ma nella parte inferiore di questo articolo è disponibile una soluzione alternativa.
exl-id: 31b7086f-a941-4682-aa07-301ac31d543b
feature: B2B, Communications
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---

# Adobe Commerce 2.4.2 B2B: il modello e-mail non aggiorna l’e-mail

Questo articolo descrive un problema noto di Adobe Commerce 2.4.2 B2B in cui l’aggiornamento di alcune informazioni in un modello e-mail non viene aggiornato nelle e-mail. Questo problema influisce sui contenuti e-mail come informazioni sul cliente, tassi di valuta, simbolo di valuta, modifica del modello e-mail, ecc. Al momento non è disponibile una soluzione, ma nella parte inferiore di questo articolo è disponibile una soluzione alternativa.

## Prodotti e versioni interessati

* Adobe Commerce on-premise 2.4.2
* Infrastruttura cloud Adobe Commerce 2.4.2
* B2B 1.3.1

## Problema

<u>Passaggi da riprodurre</u>:

1. L’amministratore della società crea un OA (ordine di acquisto) nel front-end.
1. Controlla l’e-mail Approvato automaticamente. Il **nome cliente** / **tasso di cambio** devono essere valori previsti.
1. Cambia simbolo di valuta (**Archivi > Configurazione > Impostazione divisa > Opzioni divisa**) in Amministratore e nome dell’amministratore della società nella pagina Account cliente.
1. L&#39;amministratore cliente crea un altro OA in Amministratore.
1. Controlla l’e-mail Approvato automaticamente.

<u>Risultati previsti:</u>

Il nome del cliente e il simbolo di valuta vengono modificati nelle e-mail e hanno i nuovi valori come previsto.

<u>Risultati effettivi</u>:

Il nome del cliente e il simbolo di valuta non vengono modificati nelle e-mail e hanno i loro valori precedenti.

## Soluzione alternativa

Esegui manualmente il processo cron o il consumer per propagare le nuove informazioni.

## Lettura correlata

* [Gestire le code dei messaggi](https://devdocs.magento.com/guides/v2.4/config-guide/mq/manage-message-queues.html) nella documentazione per gli sviluppatori.
