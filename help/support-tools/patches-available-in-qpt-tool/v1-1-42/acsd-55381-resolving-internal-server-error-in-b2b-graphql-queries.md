---
title: "ACSD-55381: errore di risoluzione durante la richiesta di UID di opzioni di prodotto configurabili dall’elenco delle richieste B2B"
description: Applica la patch ACSD-55381 per risolvere il problema di Adobe Commerce in cui si verifica un errore interno del server durante le query GraphQL per i campi "configurable_product_option_uid" e "configurable_product_option_value_uid" da un elenco di richieste B2B.
feature: GraphQL, B2B, Products
role: Admin, Developer
exl-id: 4e7edb8d-8be8-45c9-b9ba-ff329656312e
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-55381: errore risolutivo durante la richiesta di UID di opzioni di prodotto configurabili dall’elenco di richieste B2B

La patch ACSD-55381 risolve il problema relativo a un errore interno del server durante le query GraphQL per `configurable_product_option_uid` e `configurable_product_option_value_uid` campi da un elenco di richieste B2B. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42. L’ID della patch è ACSD-55381. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Errore interno del server durante la query `configurable_product_option_uid` e `configurable_product_option_value_uid` campi da un elenco di richieste B2B tramite GraphQL.

<u>Prerequisiti</u>:

1. I moduli B2B di Adobe Commerce vengono installati e abilitati.
1. Elenco richieste di acquisto abilitato nella configurazione.

<u>Passaggi da riprodurre</u>:

1. Accedi come cliente sulla vetrina.
1. Aggiungere un prodotto configurabile a un elenco di richieste.
1. Prova a recuperare i valori per `configurable_product_option_uid` e `configurable_product_option_value_uid` campi che utilizzano `getRequisitionList` in una chiamata GraphQL.

```
query getRequisitionList {
  customer {
    requisition_lists(filter: { uids: { eq: "MQo=" } }) {
      items {
        items(pageSize: 1, currentPage: 1) {
          items {
            ... on ConfigurableRequisitionListItem {
              configurable_options {
                value_id
                id
                configurable_product_option_uid
                configurable_product_option_value_uid
              }
            }
          }
        }
      }
    }
  }
}
```

<u>Risultati previsti</u>:

```
{
    "data": {
        "customer": {
            "requisition_lists": {
                "items": [
                    {
                        "items": {
                            "items": [
                                {
                                    "configurable_options": [
                                        {
                                            "value_id": 175,
                                            "id": 186,
                                            "configurable_product_option_uid": "MTg2",
                                            "configurable_product_option_value_uid": "MTc1"
                                        },
                                        {
                                            "value_id": 58,
                                            "id": 93,
                                            "configurable_product_option_uid": "OTM=",
                                            "configurable_product_option_value_uid": "NTg="
                                        }
                                    ]
                                }
                            ]
                        }
                    }
                ]
            }
        }
    }
}
```

<u>Risultati effettivi</u>:

Si verifica un errore.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
