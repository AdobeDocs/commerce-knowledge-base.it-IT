---
title: Come rimuovere Magento Order Management (MOM)
description: Questo articolo spiega come rimuovere il sistema Magento Order Management (MOM).
exl-id: 9b2adb30-a880-45a2-859e-be0da42bfd07
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%
---
# Come rimuovere Magento Order Management (MOM)

1. Disattivare l&#39;integrazione MOM seguendo la procedura descritta in [Disattivare o attivare l&#39;integrazione](https://commerce-docs.github.io/oms-documentation-archive/integration/connector/#disable-or-enable-the-integration).
1. Disattivare il modulo MOM seguendo la procedura descritta in [Moduli di disinstallazione](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).
1. Per l’estrazione dei dati dell’ordine completo, offriamo l’API. Per saperne di più, consulta [Archivio ordini](https://commerce-docs.github.io/oms-documentation-archive/specifications/#magento.sales.order_repository) nel nostro Adobe | Documentazione OMS di Magento, che riguarda le informazioni sull’ordine (order_repository). Utilizza la [sezione delle specifiche](https://commerce-docs.github.io/oms-documentation-archive/specifications/#services) nel nostro Adobe | Magento OMS Docs per utilizzare altre API per estrarre diversi tipi di informazioni.
