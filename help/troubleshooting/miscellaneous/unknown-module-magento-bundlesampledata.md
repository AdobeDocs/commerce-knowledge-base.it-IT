---
title: Modulo sconosciuto Magento_BundleSampleData
description: Questo articolo fornisce una correzione per l’errore sconosciuto del modulo durante l’installazione di Adobe Commerce.
exl-id: c927bc8f-d70b-4305-87c1-223001212555
feature: Extensions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---

# Modulo sconosciuto Magento_BundleSampleData

Questo articolo fornisce una correzione per l’errore sconosciuto del modulo durante l’installazione di Adobe Commerce.

## Problema {#details}

Durante l’installazione viene visualizzato un messaggio simile al seguente:

```text
[ERROR] exception 'LogicException' with message 'Unknown module in the requested list: 'Magento_BundleSampleData''
```

## Soluzione {#solution}

Provare a eseguire una delle seguenti operazioni alla volta, quindi ripetere l&#39;installazione.

1. Eseguire l&#39;Installazione guidata Web. I moduli sono elencati in  **Configurazioni moduli avanzate**. Per disattivare **Magento\_BundleSampleData** , cancella il **Magento\_BundleSampleData** come illustrato nella figura seguente.

   ![tshoot_bundlesampledata.png](assets/tshoot_bundlesampledata.png)

1. Cancella tutti i dati e la cronologia del browser dal browser.
1. Se disponi di Chrome, cancella tutti i dati del browser relativi al tuo sito.  Vai a **Impostazioni** > **Opzioni avanzate** > **Privacy** > **Impostazioni contenuto** > **Tutti i cookie e i dati del sito**. Nella colonna Sito, fai clic sull’indirizzo del server Adobe Commerce e fai clic su **Rimuovi tutto**.
