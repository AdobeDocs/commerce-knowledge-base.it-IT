---
title: "B2B: le aziende non possono accedere alle pagine di profilo sulla vetrina"
description: Questo articolo fornisce una patch per il problema noto di Adobe Commerce 2.2.4 B2B relativo alle aziende registrate che ricevono errori sulle pagine dell’account nella vetrina.
exl-id: 5f0d81a2-e0a1-487b-8a4f-28b8cb704e32
feature: B2B, Companies
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---

# B2B: le aziende non possono accedere alle pagine di profilo sul lato negozio

Questo articolo fornisce una patch per il problema noto di Adobe Commerce 2.2.4 B2B relativo alle aziende registrate che ricevono errori sulle pagine dell’account nella vetrina.

## Problema

I clienti (aziende) possono creare un account aziendale sul sito, ma ottenere il messaggio di errore *&quot;Nessuna entità di questo tipo con customerId = &quot;* e *&quot;Non si dispone ancora di un account aziendale&quot;*. È inoltre possibile che ricevano *&quot;500 Internal Server Error&quot;* quando tentano di accedere alla pagina del profilo aziendale.

## Patch

Per scaricare l’archivio con una patch, fai clic sul seguente collegamento:

[Scarica MDVA-9013\_EE\_2.2\_compositore.patch](assets/MDVA-9013_EE_2.2.2_composer.patch.zip)

### Versioni compatibili di Adobe Commerce

La patch è stata creata per:

* Adobe Commerce on-premise 2.2.2

La patch è compatibile (ma potrebbe non risolvere il problema) anche con le seguenti versioni ed edizioni di Adobe Commerce:

* Adobe Commerce sull’infrastruttura cloud da 2.2.0 a 2.2.4
* Adobe Commerce on-premise da 2.2.0 a 2.2.1 e da 2.2.3 a 2.2.4

## Come applicare il cerotto

Per istruzioni, vedere [Come applicare una patch del compositore fornita dall&#39;Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md).
