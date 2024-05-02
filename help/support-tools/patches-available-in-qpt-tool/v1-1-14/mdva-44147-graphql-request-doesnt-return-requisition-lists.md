---
title: "MDVA-44147: la richiesta di GraphQL non restituisce gli elenchi di richieste di acquisto"
description: La patch di MDVA-44147 risolve il problema per cui la richiesta di GraphQL non restituisce gli elenchi delle richieste di acquisto. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14. L'ID della patch è MDVA-44147. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
exl-id: c7a526f2-638c-4172-8750-aa076724851a
feature: B2B, GraphQL
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# MDVA-44147: la richiesta GraphQL non restituisce gli elenchi di richieste di acquisto

La patch di MDVA-44147 risolve il problema per cui la richiesta di GraphQL non restituisce gli elenchi delle richieste di acquisto. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14. L&#39;ID della patch è MDVA-44147. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La richiesta di GraphQL non restituisce gli elenchi di richieste.

<u>Passaggi da riprodurre</u>:

1. Vai a **Archivia** > **Impostazioni** > **Configurazione** > **Generale** > **Caratteristiche B2B** e abilita Elenco richieste di acquisto.
1. Accedi come cliente e aggiungi un prodotto alla [Elenco richieste](https://docs.magento.com/user-guide/customers/account-dashboard-requisition-lists.html).
1. Creare un [Token cliente](https://devdocs.magento.com/guides/v2.4/graphql/mutations/generate-customer-token.html).

   <pre>
    <code class="language-graphql">
    mutation {
      generateCustomerToken(
        email: "test@gmail.com"
        password: "xxxxxxxx"
        ) {
          token
        }
      }
      </code>
      </pre>

1. Utilizzare la query seguente per recuperare tutti gli elenchi di richieste dal cliente. Utilizza il **Autorizzazione** intestazione con il valore `Bearer <customer_token>`. Consulta la sezione [Query cliente](https://devdocs.magento.com/guides/v2.4/graphql/queries/customer.html) per ulteriori informazioni, consulta l’articolo nella documentazione per sviluppatori.

   Richiesta:

   <pre>
    <code class="language-graphql">
    query {
      customer {
        requisition_lists(
          pageSize: 20
          ) {
            items {
              uid
              name
              description
              items(pageSize: 20) {
                items {
                  uid
                  product {
                    uid
                    name
                    sku
                    __typename
                  }
                  quantity
                }
                total_pages
              }
            }
            total_count
          }
        }
      }
      </code>
      </pre>

   Risposta:

   <pre>
    <code class="language-graphql">
    {
      "data": {
        "customer": {
          "requisition_lists": {
            "items": [
            {
              "uid": "MQ==",
              "name": "Name",
              "description": "Description",
              "items": {
                "items": [
                {
                  "uid": "MQ==",
                  "product": {
                    "uid": "MQ==",
                    "name": "Simple 01",
                    "sku": "s00001",
                    "__typename": "SimpleProduct"
                    },
                    "quantity": 1
                  }
                  ],
                  "total_pages": 1
                }
              }
              ],
              "total_count": 1
            }
          }
        }
      }
      </code>
      </pre>

1. Copia l’UID di qualsiasi elemento dall’elenco restituito (MQ==) e utilizza la seguente query per ottenere l’elenco filtrato dall’UID.

   <pre>
    <code class="language-graphql">
    query {
      customer {
        requisition_lists(
          pageSize: 20,
          filter: {
            uids: {
              eq: "MQ=="
            }
          }
          ) {
            items {
              uid
              name
              description
              items(pageSize: 20) {
                items {
                  uid
                  product {
                    uid
                    name
                    sku
                    __typename
                  }
                  quantity
                }
                total_pages
              }
            }
            total_count
          }
        }
      }
      </code>
      </pre>

<u>Risultati previsti</u>:

Viene restituito un risultato.

<u>Risultati effettivi</u>:

Vengono restituiti zero risultati.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
