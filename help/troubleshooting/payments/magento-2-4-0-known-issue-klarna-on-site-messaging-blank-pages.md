---
title: "Problema noto di Adobe Commerce 2.4.0: pagine vuote della messaggistica in sito di Klarna"
description: Questo articolo descrive un problema noto di Adobe Commerce 2.4.0 con il metodo di pagamento Klarna, in cui l’abilitazione della messaggistica in sito di Klarna senza specificare un tema di progettazione comporta la mancata visualizzazione corretta delle pagine dei prodotti nella vetrina (le pagine dei prodotti vengono visualizzate vuote).
exl-id: f0f9edfc-eaad-4947-9200-41e217bfbe84
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---

# Problema noto di Adobe Commerce 2.4.0: pagine vuote della messaggistica in sito di Klarna

Questo articolo descrive un problema noto di Adobe Commerce 2.4.0 con il metodo di pagamento Klarna, in cui l’abilitazione della messaggistica in sito di Klarna senza specificare un tema di progettazione comporta la mancata visualizzazione corretta delle pagine dei prodotti nella vetrina (le pagine dei prodotti vengono visualizzate vuote).

## Prodotti e versioni interessati

* Adobe Commerce on-premise 2.4.0
* Adobe Commerce sull’infrastruttura cloud 2.4.0

<u>Prerequisiti:</u> il metodo di pagamento Klarna è abilitato.

<u>Passaggi da riprodurre:</u>

1. Nell&#39;amministratore di Commerce, vai a **Negozi** > **Configurazione** > **Vendite** > **Metodi di pagamento** > **Klarna** > **Messaggistica in loco Klarna**.
1. Imposta **Abilita** su *Sì*.
1. Lascia vuoto il campo **Tema progettazione**.
1. Salvare la configurazione facendo clic su **Salva configurazione**.
1. Vai alla vetrina e passa a qualsiasi pagina di prodotto.

<u>Risultato previsto:</u>

La pagina viene caricata correttamente con il tema di progettazione predefinito applicato per la messaggistica Klarna sul sito.

<u>Risultato effettivo:</u>

Viene visualizzata una pagina vuota.

## Soluzione

Se abiliti la messaggistica sul sito di Klarna, accertati sempre che il campo **Tema di progettazione** non sia vuoto.
