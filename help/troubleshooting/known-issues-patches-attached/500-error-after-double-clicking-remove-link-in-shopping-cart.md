---
title: '"Errore 500" dopo aver fatto doppio clic su Rimuovi collegamento nel carrello'
description: Questo articolo fornisce una patch per il problema noto di Adobe Commerce on cloud infrastructure 2.2.0 relativo agli errori dei clienti che si verificano quando tentano di rimuovere due volte un articolo del carrello (facendo doppio clic sul collegamento *Rimuovi* o facendo clic su di esso in diverse schede).
exl-id: 927cf681-febf-42cc-8db5-469bcf8f2012
feature: Orders, Shopping Cart
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# &quot;Errore 500&quot; dopo aver fatto doppio clic su Rimuovi collegamento nel carrello

Questo articolo fornisce una patch per il problema noto di Adobe Commerce on cloud infrastructure 2.2.0 relativo agli errori dei clienti che si verificano quando tentano di rimuovere due volte un articolo del carrello (facendo doppio clic sul collegamento *Rimuovi* o facendo clic su di esso in diverse schede).

## Problema

Quando i clienti fanno doppio clic sul collegamento *Rimuovi* nel carrello e tentano di rimuovere un prodotto dal carrello, ottengono una pagina vuota con il seguente messaggio di errore: *&quot;Questa pagina non funziona. ERRORE HTTP 500&quot;.* Lo stesso problema si verifica se un cliente apre due schede del browser con la pagina del carrello e rimuove il prodotto prima in una scheda, quindi nella seconda.

<u>Passaggi da riprodurre</u>:

1. Aggiungi un prodotto al carrello nella vetrina.
1. Passa alla pagina del carrello.
1. Fare doppio clic sul collegamento Rimuovi.

OPPURE

1. Aggiungi un prodotto al carrello nella vetrina.
1. Passa alla pagina del carrello.
1. Apri una nuova scheda del browser e passa alla pagina del carrello (stesso prodotto).
1. Rimuovi il prodotto dal carrello.
1. Apri la seconda scheda e rimuovi di nuovo il prodotto.

<u>Risultato previsto</u>: il prodotto viene rimosso dal carrello senza errori.

<u>Risultato effettivo</u>: il prodotto è stato rimosso con l&#39;errore: *&quot;Questa pagina non funziona. ERRORE HTTP 500&quot;* messaggio di errore.

## Patch

La patch è allegata a questo articolo. Per scaricarlo, scorri verso il basso fino alla fine dell’articolo e fai clic sul nome del file, oppure fai clic sul seguente collegamento:

[Scarica MDVA-8623\_EE\_2.2.0\_v1.compositore.patch](assets/MDVA-8623_EE_2.2.0_v1.composer.patch.zip)

## Versioni compatibili di Adobe Commerce:

La patch è stata creata per:

* Adobe Commerce sull’infrastruttura cloud 2.2.0

La patch è compatibile (ma potrebbe non risolvere il problema) anche con le seguenti versioni ed edizioni di Adobe Commerce:

* Adobe Commerce sull’infrastruttura cloud 2.2.1 - 2.2.5
* Adobe Commerce on-premise 2.2.0 - 2.2.5

## Come applicare il cerotto

Per istruzioni, vedere [Come applicare una patch del compositore fornita dall&#39;Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) nella Knowledge Base di supporto.

## File allegati
