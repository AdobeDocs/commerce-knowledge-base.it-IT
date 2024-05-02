---
title: Patch per il problema di pagamento Amazon in Adobe Commerce 2.3.5-p1
description: Questa patch risolve il problema dell’impossibilità di modificare un metodo di pagamento nella fase "Revisione e pagamenti" del pagamento dal widget dei pagamenti, durante il pagamento con Amazon Pay in Adobe Commerce.
exl-id: a241f67f-019c-4ff2-a5ad-e7dc71639768
feature: Checkout, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# Patch per il problema di pagamento Amazon in Adobe Commerce 2.3.5-p1

Questa patch risolve il problema dell’impossibilità di modificare un metodo di pagamento nella fase &quot;Revisione e pagamenti&quot; del pagamento dal widget dei pagamenti, durante il pagamento con Amazon Pay in Adobe Commerce.

## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud versione 2.3.5-p1
* Adobe Commerce on-premise versione 2.3.5-p1

## Problema

Quando un cliente effettua il check-out con Amazon Pay, effettua l’accesso, procede al passaggio di pagamento e tenta di modificare la propria carta di credito dal widget pagamenti, viene visualizzato un messaggio di errore. Impossibile completare l&#39;estrazione se l&#39;acquirente ignora l&#39;errore e procede all&#39;estrazione.

Per risolvere questo problema e rimuovere l’errore, è stata creata una [patch](assets/BUNDLE-2554_EE_2.3.5-p1.composer.patch.zip).

<u>Passaggi da riprodurre</u>:

1. Inizia il pagamento con Amazon Pay.
1. Accedi come cliente Amazon Pay.
1. Seleziona il metodo di spedizione e procedi alla fase di pagamento.
1. Prova a cambiare la carta di credito.

<u>Risultato previsto</u>: viene selezionata un’altra carta di credito come metodo di pagamento senza errori.

<u>Risultato effettivo</u>: viene visualizzato il messaggio di errore: *&quot;Contatta questo commerciante per completare l&#39;ordine.&quot;*

## Soluzione

[Applicare la patch](assets/BUNDLE-2554_EE_2.3.5-p1.composer.patch.zip) di seguito.

## Patch

La patch è allegata a questo articolo. Per scaricarlo, scorri verso il basso fino alla fine dell’articolo e fai clic sul nome del file, oppure fai clic sul seguente collegamento:

[Scarica BUNDLE-2554\_EE\_2.3.5-p1.compositore.patch](assets/BUNDLE-2554_EE_2.3.5-p1.composer.patch.zip)

### Versioni compatibili di Adobe Commerce:

La patch è stata creata per:

* Adobe Commerce su infrastruttura cloud versione 2.3.5-p1
* Adobe Commerce on-premise versione 2.3.5-p1

La patch è compatibile (ma potrebbe non risolvere il problema) anche con le seguenti versioni ed edizioni di Adobe Commerce:

* Adobe Commerce su infrastruttura cloud versione 2.3.5
* Adobe Commerce on-premise versione 2.3.5

## Come applicare il cerotto

Consulta [Come applicare una patch del compositore fornita da Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) nella knowledge base di supporto per le istruzioni.

## File allegati
