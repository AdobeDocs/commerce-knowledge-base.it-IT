---
title: 'Problema noto di Adobe Commerce 2.4.0: pagine vuote della messaggistica in sito di Klarna'
description: Questo articolo descrive un problema noto di Adobe Commerce 2.4.0 con il metodo di pagamento Klarna, in cui l’abilitazione della messaggistica in sito di Klarna senza specificare un tema di progettazione comporta la mancata visualizzazione corretta delle pagine dei prodotti nella vetrina (le pagine dei prodotti vengono visualizzate vuote).
exl-id: f0f9edfc-eaad-4947-9200-41e217bfbe84
feature: Orders, Payments
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '204'
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
