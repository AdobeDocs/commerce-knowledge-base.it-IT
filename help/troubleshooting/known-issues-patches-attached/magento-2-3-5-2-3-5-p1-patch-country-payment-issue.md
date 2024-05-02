---
title: "Adobe Commerce 2.3.5, 2.3.5-p1 patch: problema di pagamento del paese"
description: Questa patch risolve un problema in Adobe Commerce in cui il flusso di lavoro di pagamento della vetrina non mostrava alcun metodo di pagamento abilitato per paesi specifici, ad eccezione di Klarna e Amazon Pay.
exl-id: e205e35e-9ffe-4826-b951-3a3caf1e0621
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Adobe Commerce 2.3.5, 2.3.5-p1 patch: problema di pagamento paese

Questa patch risolve un problema in Adobe Commerce in cui il flusso di lavoro di pagamento della vetrina non mostrava alcun metodo di pagamento abilitato per paesi specifici, ad eccezione di Klarna e Amazon Pay.

## Prodotti e versioni interessati

* Adobe Commerce sull’infrastruttura cloud 2.3.5 e 2.3.5-p1
* Adobe Commerce on-premise 2.3.5 e 2.3.5-p1

## Problema

Quando un negozio ha Amazon Pay e un altro pagamento assegnato a paesi diversi, e quando uno di questi paesi e metodi di pagamento è selezionato, il metodo di pagamento e i pulsanti Inserisci ordine non sono visibili.

L’aggiornamento di una pagina web rappresenta una soluzione a questo problema.

Per risolvere questo problema e rimuovere l’errore, è stata creata una [patch](assets/BUNDLE-2546_EE_2.3.5-p1.composer.patch.zip).

<u>Prerequisiti</u>:

* Viene creato un prodotto semplice.
* **Assegno/vaglia postale** è abilitato solo per paesi specifici (at **Archivia** > **Configurazione** > **Vendite** > **Metodi di pagamento**).

* Esempio: Pagamento da paesi applicabili = paesi specifici
* Esempio: Pagamento da paesi specifici = Regno Unito

<u>Passaggi da riprodurre</u>:

1. Vai alla vetrina come ospite.
1. Aggiungi un prodotto semplice al carrello.
1. Vai a Pagamento.
1. Compila il modulo con dati validi.

   * Paese = *Stati Uniti*

1. Seleziona la tariffa di spedizione e fai clic su **Successivo**.

   * La fase di pagamento è aperta.
   * Nessun pagamento disponibile.
   * Messaggio: **Nessun metodo di pagamento disponibile.**
   * Non esiste **Inserisci ordine** pulsante.

1. Torna a **Passaggio di spedizione** e modifica il valore in:

   * Paese = *Regno Unito*

1. Seleziona la tariffa di spedizione e fai clic su **Successivo**.

<u>Risultato previsto</u>:

Viene visualizzata la fase Pagamento.

* **Consegna contanti** viene visualizzato.
* **Assegno/vaglia postale** viene visualizzato.
* Il **Inserisci ordine** viene visualizzato.

<u>Risultato effettivo</u>:

Viene visualizzata la fase Pagamento.

* Nessun pagamento disponibile.
* Messaggio: *Nessun metodo di pagamento disponibile.*
* Non esiste **Inserisci ordine** pulsante.

## Soluzione

[Applicare la patch](assets/BUNDLE-2546_EE_2.3.5-p1.composer.patch.zip) di seguito.

## Patch

La patch è allegata a questo articolo. Per scaricarlo, scorri verso il basso fino alla fine dell’articolo e fai clic sul nome del file o sul seguente collegamento:

[Scarica BUNDLE-2546\_EE\_2.3.5-p1.compositore.patch](assets/BUNDLE-2546_EE_2.3.5-p1.composer.patch.zip)

### Versioni compatibili di Adobe Commerce:

La patch è stata creata per:

* Adobe Commerce sull’infrastruttura cloud 2.3.5 e 2.3.5-p1
* Adobe Commerce on-premise 2.3.5 e 2.3.5-p1

La patch è compatibile (ma potrebbe non risolvere il problema) anche con le seguenti versioni ed edizioni di Adobe Commerce:

* Adobe Commerce versioni 2.3.4-p2 - 2.2.6

## Come applicare il cerotto

Consulta [Come applicare una patch del compositore fornita da Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) nella knowledge base di supporto per le istruzioni.

## File allegati
