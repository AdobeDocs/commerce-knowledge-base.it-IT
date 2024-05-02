---
title: "MDVA-35569: FPT non verrà visualizzato in GraphQL"
description: La patch MDVA-35569 risolve il problema quando FPT (fixed product tax, imposta sul prodotto fissa) non viene visualizzato in GraphQL quando lo stato è specificato nel carrello. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19. L'ID della patch è MDVA-35569. Il problema è stato risolto nella versione 2.4.3 di Adobe Commerce.
exl-id: 3c38f7f9-9372-4f22-819c-c53efb9b5f78
feature: GraphQL
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# MDVA-35569: impossibile visualizzare FPT in GraphQL

La patch MDVA-35569 risolve il problema quando FPT (fixed product tax, imposta sul prodotto fissa) non viene visualizzato in GraphQL quando lo stato è specificato nel carrello. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19. L&#39;ID della patch è MDVA-35569. Il problema è stato risolto nella versione 2.4.3 di Adobe Commerce.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.3.4-p2

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.3.4-2.4.1-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Passaggi da riprodurre</u>:

1. Abilita FPT.
1. Creare un attributo (esempio: *weee\_tax*).
1. Creare un prodotto di prova (ad esempio: *Weetax*) con *weee\_tax* attributo aggiunto.
1. Assegnare FPT alla California o a un altro stato del *weee\_tax* attributo.
1. Creare un cliente in GraphQL.
1. Crea un carrello in GraphQL.
1. Aggiungi il *ascia* al carrello con GraphQL.
1. Eseguire una query sul carrello:

```php
{cart(cart_id: "xxx") {    items {    id    product {    name    sku    price_range {    minimum_price {    final_price {    value    }    fixed_product_taxes {    label    amount {    value    }    }    }    maximum_price {    final_price {    value    }    fixed_product_taxes {    label    amount {    value    }    }    }    }    }    prices {    price {    value    }    }    quantity    }    prices {    subtotal_excluding_tax {    value    }    applied_taxes {    amount {    value    }    }    grand_total {    value    currency    }    discounts {    amount {    value    }    label    }    }}}
```

<u>Risultati previsti</u>:

L’FPT sarebbe popolato normalmente, come previsto.

<u>Risultati effettivi</u>:

* L’FPT non viene compilato con i dati ed è vuoto.
* La query sul carrello fornisce questa risposta:

```php
{
 "data": {
 "cart": {
 "items": [
 {
 "id": "1",
 "product": {
 "name": "fpt",
 "sku": "fpt",
 "price_range": {
 "minimum_price": {
 "final_price": {
 "value": 10
 },
 "fixed_product_taxes": []
 },
 "maximum_price": {
 "final_price": {
 "value": 10
 },
 "fixed_product_taxes": []
 }
 }
 },
 "prices": {
 "price": {
 "value": 10
 }
 },
 "quantity": 1
 }
 ],
 "prices": {
 "subtotal_excluding_tax": {
 "value": 10
 },
 "applied_taxes": [],
 "grand_total": {
 "value": 21,
 "currency": "USD"
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
