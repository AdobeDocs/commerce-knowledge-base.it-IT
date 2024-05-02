---
title: Data errata per il prezzo speciale
description: Questo articolo fornisce una patch per il problema noto di Adobe Commerce 2.2.2 relativo alla data "da" del prezzo speciale del prodotto, che non è corretta se il suo valore viene modificato dall’amministratore con impostazioni internazionali di interfaccia diverse.
exl-id: fc109550-951e-4900-97e3-4ff3e7e5a395
feature: Orders, Personalization, User Account
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# Data errata per il prezzo speciale

Questo articolo fornisce una patch per il problema noto di Adobe Commerce 2.2.2 relativo alla data &quot;da&quot; del prezzo speciale del prodotto, che non è corretta se il suo valore viene modificato dall’amministratore con impostazioni internazionali di interfaccia diverse.

## Problema

Quando si imposta o si modifica il prezzo speciale di un prodotto, la data e l&#39;ora correnti vengono salvate nel database come valore per `special_from_date` (non visibile durante la modifica di un prodotto). Se modifichi il prezzo speciale e l’account utente amministratore è impostato su una lingua diversa nell’interfaccia, è possibile che venga impostato un valore errato `special_from_date` a causa di problemi nel formato della data di analisi per diverse impostazioni internazionali.

<u>Passaggi da riprodurre</u>:

Prerequisiti: le impostazioni locali dell&#39;utente amministratore sono inglese (Stati Uniti).

1. Accedi all’amministratore di Commerce.
1. Passa alle impostazioni dell’account utente amministratore.
1. Impostare Interfaccia locale su Ucraino.
1. Clic **Salva account**.
1. Vai a **Catalogo** > **Prodotto**.
1. Seleziona un prodotto.
1. Nella pagina del prodotto, fai clic su **Advanced Pricing**.
1. Aggiungi un prezzo speciale.
1. Salva il prodotto.
1. Ripetere i passaggi 7-9.
1. Vai a **Sistema** > **Registri azioni**.
1. Controlla il registro per informazioni sull’aggiornamento del prodotto.

<u>Risultati previsti</u>:

La data di inizio del prezzo speciale deve essere la data corrente.

<u>Risultati effettivi</u>:

La data di inizio per il prezzo speciale è una data di alcuni anni nel futuro, impedendo al prezzo speciale di essere attivo.

## Soluzione

L’applicazione della patch evita che il problema si ripresenti. Per correggere i dati relativi ai prodotti in cui la data è stata impostata in modo errato, impostare nuovamente il prezzo speciale dopo aver applicato la patch.

## Patch

La patch è allegata a questo articolo. Per scaricarlo, scorri verso il basso fino alla fine dell’articolo e fai clic sul nome del file o sul seguente collegamento:

[Scarica MDVA-11605\_EE\_2.2\_COMPOSER\_v1.patch](assets/MDVA-11605_EE_2.2.2_COMPOSER_v1.patch.zip)

### Versioni compatibili di Adobe Commerce:

La patch è stata creata per:

* Adobe Commerce (tutti i metodi di implementazione) 2.2.2

La patch è compatibile (ma potrebbe non risolvere il problema) anche con le seguenti versioni ed edizioni di Adobe Commerce:

* Adobe Commerce on-premise 2.1.0-2.1.18, 2.2.0-2.2.5
* Adobe Commerce sull’infrastruttura cloud 2.1.11-2.1.18, 2.2.0-2.2.5

## Come applicare il cerotto

Consulta [Come applicare una patch del compositore fornita da Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) per istruzioni.

## File allegati
