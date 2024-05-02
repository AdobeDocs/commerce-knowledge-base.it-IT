---
title: Problema relativo al carrello vuoto quando si fa clic più volte al momento del pagamento dal mini carrello
description: Questo articolo fornisce una patch per un problema noto di Adobe Commerce 2.2.3 relativo a un carrello vuoto dopo che i clienti hanno fatto clic più volte su **Vai al pagamento** nel mini carrello.
exl-id: 06b82c91-8998-4e7b-9fc0-671c9b2a2d3f
feature: Checkout, Orders, Shopping Cart
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---

# Problema relativo al carrello vuoto quando si fa clic più volte al momento del pagamento dal mini carrello

Questo articolo fornisce una patch per un problema noto di Adobe Commerce 2.2.3 relativo a un carrello vuoto dopo che i clienti hanno fatto clic su **Vai a Pagamento** più volte nel mini carrello.

## Problema

I clienti aggiungono prodotti al carrello, prova a effettuare il pagamento facendo clic sul pulsante **Vai a Pagamento** più volte, ma quando vanno al carrello, il carrello è vuoto. Il mini-carrello potrebbe ancora mostrare i prodotti.

<u>Passaggi da riprodurre</u> :

1. Apri una pagina di prodotto sulla vetrina.
1. Aggiungi prodotti al carrello.
1. Nel mini carrello, fai clic su **Vai a Pagamento** più volte.

<u>Risultato previsto</u> :

Il carrello contiene tutti i prodotti aggiunti.

<u>Risultato effettivo</u> :

Non hai alcun articolo nel carrello.

## Patch

Le patch sono allegate a questo articolo. Per scaricare una patch, scorri verso il basso fino alla fine dell’articolo e fai clic sul nome del file richiesto oppure su uno dei seguenti collegamenti:

[Scarica MDVA-10441\_EE\_2.2.3\_v3.compositore.patch](assets/MDVA-10441_EE_2.2.3_v3.composer.patch.zip)

[Scarica MDVA-17078\_EE\_2.2.5\_COMPOSER\_v1.patch](assets/MDVA-17078_EE_2.2.5_COMPOSER_v1.patch.zip)

### Versioni compatibili di Adobe Commerce

Le patch sono state create per:

* Adobe Commerce on-premise 2.2.3 `MDVA-10441_EE_2.2.3_v3.composer.patch` file)
* Adobe Commerce sull’infrastruttura cloud 2.2.5 (`MDVA-17078_EE_2.2.5_COMPOSER_v1.patch` file)

Il `MDVA-10441_EE_2.2.3_v3.composer.patch` La patch è compatibile (ma potrebbe non risolvere il problema) anche con le seguenti versioni ed edizioni di Adobe Commerce:

* Versioni di Adobe Commerce su infrastruttura cloud da 2.2.1 a 2.2.5
* Versioni di Adobe Commerce on-premise da 2.2.1 a 2.2.5

Il `MDVA-17078_EE_2.2.5_COMPOSER_v1.patch` La patch è compatibile (ma potrebbe non risolvere il problema) anche con le seguenti versioni ed edizioni di Adobe Commerce:

* Adobe Commerce 2.2.5

## Come applicare una patch

Per istruzioni, consulta [Come applicare una patch del compositore fornita dall&#39;Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) nella nostra knowledge base di supporto.

## File allegati
