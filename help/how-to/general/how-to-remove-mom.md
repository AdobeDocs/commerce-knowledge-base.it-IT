---
title: Come rimuovere Magento Order Management (MOM)
description: Questo articolo spiega come rimuovere il sistema Magento Order Management (MOM).
exl-id: 9b2adb30-a880-45a2-859e-be0da42bfd07
source-git-commit: 724a30310c3841f8280628436925f9a3e5933b14
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---

# Come rimuovere Magento Order Management (MOM)

1. Disattivare l&#39;integrazione MOM seguendo la procedura descritta in [Disattivare o attivare l&#39;integrazione](https://commerce-docs.github.io/oms-documentation-archive/integration/connector/#disable-or-enable-the-integration).
1. Disattivare il modulo MOM seguendo la procedura descritta in [Moduli di disinstallazione](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).
1. Per l’estrazione dei dati dell’ordine completo, offriamo l’API. Per saperne di più, consulta [Archivio ordini](https://commerce-docs.github.io/oms-documentation-archive/specifications/#magento.sales.order_repository) nel nostro Adobe | Documentazione di Magento OMS, relativa alle informazioni sull&#39;ordine (order_repository). Utilizza la [sezione delle specifiche](https://commerce-docs.github.io/oms-documentation-archive/specifications/#services) nel nostro Adobe | Documentazione di Magento OMS per utilizzare altre API per estrarre diversi tipi di informazioni.
