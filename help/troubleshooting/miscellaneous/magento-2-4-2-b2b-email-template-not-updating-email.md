---
title: 'Adobe Commerce 2.4.2 B2B: il modello e-mail non aggiorna l’e-mail'
description: Questo articolo descrive un problema noto di Adobe Commerce 2.4.2 B2B in cui l’aggiornamento di alcune informazioni in un modello e-mail non viene aggiornato nelle e-mail. Questo problema influisce sui contenuti e-mail come informazioni sul cliente, tassi di valuta, simbolo di valuta, modifica del modello e-mail, ecc. Al momento non è disponibile una soluzione, ma nella parte inferiore di questo articolo è disponibile una soluzione alternativa.
exl-id: 31b7086f-a941-4682-aa07-301ac31d543b
feature: B2B, Communications
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bb03f6c4-cab9-560e-9d02-5816e1808d17
    internal-label: Communications
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '286'
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
1. Controlla l’e-mail Approvato automaticamente. Il **nome cliente** / **tasso di valuta** deve essere un valore previsto.
1. Modificare il simbolo di valuta (**Archivi > Configurazione > Impostazione valuta > Opzioni valuta**) nel nome dell&#39;amministratore e della società nella pagina Account cliente.
1. L&#39;amministratore cliente crea un altro OA in Amministratore.
1. Controlla l’e-mail Approvato automaticamente.

<u>Risultati previsti:</u>

Il nome del cliente e il simbolo di valuta vengono modificati nelle e-mail e hanno i nuovi valori come previsto.

<u>Risultati effettivi</u>:

Il nome del cliente e il simbolo di valuta non vengono modificati nelle e-mail e hanno i loro valori precedenti.

## Soluzione alternativa

Esegui manualmente il processo cron o il consumer per propagare le nuove informazioni.

## Lettura correlata

* [Gestisci le code dei messaggi](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/message-queues/manage-message-queues) nella documentazione per gli sviluppatori.
