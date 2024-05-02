---
title: Indirizzo di spedizione non salvato dopo l'aggiornamento della pagina al momento del pagamento
description: Questo articolo fornisce una patch per il problema noto di Adobe Commerce 2.2.3, in cui il modulo dell’indirizzo di spedizione già popolato del cliente era vuoto dopo l’aggiornamento della pagina del browser al momento del pagamento come ospite. Il problema si verificava quando il carrello acquisti persistente era abilitato.
exl-id: b757e4af-7b1a-41bc-8460-9a6858c7aa5e
feature: Checkout, Orders, Shipping/Delivery
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# Indirizzo di spedizione non salvato dopo l&#39;aggiornamento della pagina al momento del pagamento

Questo articolo fornisce una patch per il problema noto di Adobe Commerce 2.2.3, in cui il modulo dell’indirizzo di spedizione già popolato del cliente era vuoto dopo l’aggiornamento della pagina del browser al momento del pagamento come ospite. Il problema si verificava quando il carrello acquisti persistente era abilitato.

## Problema

I clienti effettuano il checkout guest e compilano tutti i moduli, incluso l&#39;indirizzo di spedizione. Arrivano alla sezione Revisione e pagamenti e ricaricano la pagina. Il modulo è vuoto ed è necessario reimmettere l&#39;indirizzo di spedizione. La funzionalità carrello acquisti persistente è abilitata.

<u>Passaggi da riprodurre</u> :

**Prerequisiti**: la funzionalità del carrello acquisti permanente è abilitata. Verifica se è abilitato in Amministratore, in **Negozi** > **Configurazione** > **Clienti** o **Negozi** > **Configurazione** > **Vendite,** a seconda della versione di Adobe Commerce.

1. Vai alla vetrina.
1. Aggiungi prodotti al carrello.
1. Procedi al pagamento come ospite.
1. Compila il tuo indirizzo di spedizione, scegli le opzioni di spedizione e continua a proteggere il pagamento.
1. Viene reindirizzato alla sezione Revisione e pagamenti del pagamento del pagamento.
1. Verificare che l&#39;indirizzo di spedizione sia visualizzato nella sezione Spedisci a.
1. Aggiorna la pagina.

<u>Risultato previsto</u>:

Puoi continuare l’estrazione e tutti i dati vengono salvati.

<u>Risultato effettivo</u>:

L&#39;indirizzo di spedizione è vuoto, è necessario affittarlo.

## Patch

La patch è allegata a questo articolo. Per scaricarlo, scorri verso il basso fino alla fine dell’articolo e fai clic sul nome del file, oppure fai clic sul seguente collegamento:

[Scarica MDVA-9718\_EE\_2.2.3\_COMPOSER\_v1.patch](assets/MDVA-9718_EE_2.2.3_COMPOSER_v1.patch.zip)

### Versioni compatibili di Adobe Commerce

**La patch è stata creata per:**

* Adobe Commerce 2.2.3

**La patch è compatibile (ma potrebbe non risolvere il problema) anche con le seguenti versioni ed edizioni di Adobe Commerce:**

* Adobe Commerce sull’infrastruttura cloud 2.1.13 - 2.1.18
* Adobe Commerce sull’infrastruttura cloud 2.2.0 - 2.2.5
* Adobe Commerce on-premise 2.0.X
* Adobe Commerce on-premise 2.1.X
* Adobe Commerce on-premise 2.2.0 - 2.2.2 e 2.2.4 - 2.2.5

## Come applicare il cerotto

Per istruzioni, consulta [Come applicare una patch del compositore fornita dall&#39;Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) nella nostra knowledge base di supporto.

## File allegati
