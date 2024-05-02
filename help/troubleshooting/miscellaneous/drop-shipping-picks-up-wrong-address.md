---
title: Ritira spedizione diretta all'indirizzo errato
description: La soluzione di spedizione non rileva l'indirizzo dell'origine del prodotto.
exl-id: ce89713f-d506-4e4f-bf49-cdee3e6d29b5
feature: Customer Service, Orders, Shipping/Delivery
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 0%

---

# Ritira spedizione diretta all&#39;indirizzo errato

## Problema

La soluzione di spedizione non rileva l&#39;indirizzo dell&#39;origine del prodotto.

## Prodotti e versioni interessati

* Adobe Commerce sull’infrastruttura cloud (tutte le versioni), con inventario Magento installato
* Adobe Commerce on-premise 2.3.0 e versioni successive, con inventario Magento installato
* Magento Open Source 2.3.0 e versioni successive, con Inventario Magenti installato

### Causa

Al momento Magento Inventory non supporta l&#39;utilizzo del calcolo delle tariffe di spedizione dirette in base all&#39;indirizzo di origine durante il pagamento. Viene invece utilizzato in tutti i casi l’indirizzo di archiviazione predefinito della configurazione.

## Lettura correlata

* [Domande frequenti sull’inventario del Magento](https://github.com/magento/inventory/wiki/MSI-FAQs) in GitHub.
