---
title: Come rimuovere il Magento Order Management (MOM)
description: Questo articolo spiega come rimuovere il Magento Order Management (MOM).
exl-id: 9b2adb30-a880-45a2-859e-be0da42bfd07
source-git-commit: 77f41d6034f985794e5c5b89cc007a69858683b9
workflow-type: tm+mt
source-wordcount: '101'
ht-degree: 0%

---

# Come rimuovere il Magento Order Management (MOM)

1. Disattivare l&#39;integrazione MOM seguendo la procedura descritta in [Disattivare o attivare l&#39;integrazione](https://commerce-docs.github.io/oms-documentation-archive/integration/connector/#disable-or-enable-the-integration).
1. Disattivare il modulo MOM seguendo la procedura descritta in [Moduli di disinstallazione](/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).
1. Per l’estrazione dei dati dell’ordine completo, offriamo l’API. Per ulteriori informazioni, consulta il [Archivio ordini](https://commerce-docs.github.io/oms-documentation-archive/specifications/#magento.sales.order_repository) nel nostro Adobe | Documenti OMS di Magento, che includono le informazioni sull&#39;ordine (order_repository). Utilizza la [sezione delle specifiche](https://commerce-docs.github.io/oms-documentation-archive/specifications/#services) nel nostro Adobe | Magento di documenti OMS per utilizzare altre API per estrarre diversi tipi di informazioni.
