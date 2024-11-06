---
title: Problema noto relativo al confronto dei prodotti in Adobe Commerce 2.3.5
description: Questo articolo fornisce consigli su come evitare un problema noto [di confronto dei prodotti](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/shopper-tools/product-compare) in Adobe Commerce on-premise 2.3.5 e Adobe Commerce on cloud infrastructure 2.3.5.
exl-id: 1488e2db-4a5d-4963-b48e-b84f760582d1
feature: Products, Storefront
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# Problema noto relativo al confronto dei prodotti in Adobe Commerce 2.3.5

Questo articolo fornisce consigli su come evitare un problema noto di [confronto dei prodotti](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/shopper-tools/product-compare) in Adobe Commerce on-premise 2.3.5 e Adobe Commerce on cloud infrastructure 2.3.5.

## Prodotti e versioni interessati

* Adobe Commerce on-premise 2.3.5
* Adobe Commerce sull’infrastruttura cloud 2.3.5

## Problema

Quando un utente tenta di confrontare prodotti provenienti da diverse visualizzazioni dello store e un prodotto ha un valore vuoto per un attributo comparabile, Adobe Commerce mostra una pagina Confronta prodotti danneggiata.

## Soluzione

Specifica valori non vuoti per attributi di prodotto comparabili o utilizza il valore predefinito per la visualizzazione archivio dell’attributo. I valori degli attributi confrontabili non possono essere vuoti.

>[!NOTE]
>
>Gli attributi del prodotto sono impostati per essere utilizzati per il confronto utilizzando l&#39;impostazione di configurazione **Comparabile su Storefront**. Per ulteriori informazioni, consulta [Creazione di attributi del prodotto](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create#step-4-describe-the-storefront-properties) nella nostra guida utente.

Una correzione sarà disponibile in Adobe Commerce 2.3.6, il cui rilascio è pianificato per il quarto trimestre del 2020.

È possibile visualizzare la correzione in GitHub (si prega di considerare che la correzione non è stata sottoposta a test di regressione e non è un hotfix ufficiale): <https://github.com/magento/magento2/pull/27662>

## Lettura correlata

<ul><li>Articoli della Knowledge Base di supporto Adobe Commerce per i problemi noti di Adobe Commerce 2.3.5:<ul>
<li>
<p title="Ordini con spedizione multipla con un prodotto virtuale non elaborati correttamente in Adobe Commerce 2.3.5"><a href="/help/troubleshooting/miscellaneous/magento-2-3-5-known-issue-virtual-product-multi-ship-orders.md">Ordini con spedizione multipla con un prodotto virtuale non elaborati correttamente in Adobe Commerce 2.3.5</a></p>
</li>
<li><a href="/help/troubleshooting/miscellaneous/bulk-action-product-count-known-issue-in-magento-2-3-5.md">Problema noto relativo al conteggio dei prodotti per azioni in blocco in Adobe Commerce 2.3.5</a></li>
<li>
<p title="Problema del metodo di pagamento nazionale in Adobe Commerce sull’infrastruttura cloud e Adobe Commerce on-premise 2.3.5 e 2.3.5-p1"><a href="/help/troubleshooting/known-issues-patches-attached/magento-2-3-5-2-3-5-p1-patch-country-payment-issue.md">Problema del metodo di pagamento nazionale in Adobe Commerce sull’infrastruttura cloud e Adobe Commerce on-premise 2.3.5 e 2.3.5-p1</a></p>
</li>
<li>
<p title="Patch per il problema di pagamento Amazon in Adobe Commerce 2.3.5-p1"><a href="/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md">Patch per il problema di pagamento Amazon in Adobe Commerce 2.3.5-p1</a></p>
</li>
</ul>
</li><li><a href="https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues">Problemi noti di Adobe Commerce 2.3.5</a> nella documentazione per gli sviluppatori</li></ul>
