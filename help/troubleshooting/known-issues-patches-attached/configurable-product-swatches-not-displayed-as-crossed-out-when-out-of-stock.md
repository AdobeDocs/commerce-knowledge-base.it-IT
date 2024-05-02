---
title: Campioni di prodotto configurabili non visualizzati barrati quando esauriti
description: Questo articolo fornisce una patch per il problema noto di Adobe Commerce 2.2.2 relativo ai campioni di prodotto configurabili esauriti che non vengono visualizzati come barrati sulla vetrina.
exl-id: 79c59a3f-a94b-4726-8af1-5fe754ea95a5
feature: Configuration, Orders, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# Campioni di prodotto configurabili non visualizzati barrati quando esauriti

Questo articolo fornisce una patch per il problema noto di Adobe Commerce 2.2.2 relativo ai campioni di prodotto configurabili esauriti che non vengono visualizzati come barrati sulla vetrina.

## Problema

Quando si dispone di un prodotto configurabile e per una determinata combinazione di opzioni, il prodotto semplice correlato non è disponibile, il campione è ancora disponibile e può essere selezionato nella vetrina.

<u>Passaggi da riprodurre</u>:

1. In Commerce Admin, crea un prodotto configurabile con opzioni per due attributi: colore (rosso, nero) e dimensione (S, M, L).
1. Impostare Quantità come &quot;1&quot; per ogni prodotto semplice corrispondente.
1. Nella vetrina, aggiungi il prodotto M rosso al carrello e fai il checkout.
1. Nell&#39;amministratore, elaborare l&#39;ordine in modo che la quantità dell&#39;articolo venga aggiornata a &quot;0&quot;.
1. Assicurati che gli ordini inevasi non siano consentiti.
1. Nella vetrina, passa alla stessa pagina di prodotto e seleziona le stesse opzioni: rosso, M.

<u>Risultati previsti</u>:

Il campione rosso, M ha una barra rossa e non può essere selezionato.

<u>Risultati effettivi</u>:

È possibile selezionare il campione M rosso.

## Patch

La patch è allegata a questo articolo. Per scaricarlo, scorri verso il basso fino alla fine dell’articolo e fai clic sul nome del file o sul seguente collegamento:

[Scarica MDVA-8215\_EE\_2.2\_v1.compositore.patch](assets/MDVA-8215_EE_2.2.2_v1.composer.patch.zip)

### Versioni compatibili di Adobe Commerce:

La patch è stata creata per:

* Adobe Commerce (tutti i metodi di implementazione) 2.2.2

La patch è compatibile (ma potrebbe non risolvere il problema) anche con le seguenti versioni ed edizioni di Adobe Commerce:

* Adobe Commerce on-premise e Adobe Commerce sull’infrastruttura cloud 2.2.0-2.2.3

## Come applicare il cerotto

Consulta [Come applicare una patch del compositore fornita da Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) per istruzioni.

## File allegati
