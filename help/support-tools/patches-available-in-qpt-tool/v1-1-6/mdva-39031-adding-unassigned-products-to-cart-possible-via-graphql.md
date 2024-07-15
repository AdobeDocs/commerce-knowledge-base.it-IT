---
title: "MDVA-39031: è possibile aggiungere prodotti non assegnati al carrello tramite GraphQL"
description: La patch MDVA-39031 risolve il problema che rende possibile l'aggiunta di un prodotto al carrello tramite GraphQL anche se non è assegnato al sito Web di destinazione. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6. L'ID della patch è MDVA-39031. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
exl-id: 5bbd64d1-06ae-4cab-a20e-0e5e5807742b
feature: GraphQL, Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# MDVA-39031: è possibile aggiungere prodotti non assegnati al carrello tramite GraphQL

La patch MDVA-39031 risolve il problema che rende possibile l&#39;aggiunta di un prodotto al carrello tramite GraphQL anche se non è assegnato al sito Web di destinazione. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6. L&#39;ID della patch è MDVA-39031. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’aggiunta di un prodotto al carrello tramite GraphQL è possibile anche se non è assegnato al sito web di destinazione.

<u>Passaggi da riprodurre</u>:

1. Crea un sito Web secondario.
1. Crea un prodotto e assegnalo al sito web principale.
1. Crea un carrello vuoto per il sito web secondario utilizzando GraphQL.

   <pre>
    <code class="language-graphql">
    mutation{
     createEmptyCart
    }
    </code>
    </pre>

   Con intestazioni come:

   <pre>
    <code class="language-graphql">
    {
      "Store":"en_au"
    }
    </code>
    </pre>

1. Aggiungi il prodotto assegnato al sito web principale al carrello nel sito web secondario.

   <pre>
    <code class="language-graphql">
    mutation {
      addProductsToCart(
          cartId: "XHrUN2nJ37OqDByhtL0VC8OxYsEZs41c"
          cartItems: [
            {
              quantity: 1
              sku: "p1"
            }
          ]
        ) {
          cart {
           items {
            product {
              name
              sku
            }
            quantity
          }
        }
      }
    }
    </code>
    </pre>

   Intestazioni

   <pre>
    <code class="language-graphql">
    {
      "Store":"en_au"
    }
    </code>
    </pre>

<u>Risultati previsti</u>:

Il prodotto non viene aggiunto al carrello perché non è stato assegnato al negozio definito nell’intestazione.

<u>Risultati effettivi</u>:

Il prodotto viene aggiunto correttamente al carrello.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
