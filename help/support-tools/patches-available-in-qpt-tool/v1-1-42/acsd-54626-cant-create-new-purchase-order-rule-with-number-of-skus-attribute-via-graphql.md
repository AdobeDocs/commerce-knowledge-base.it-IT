---
title: "ACSD-54626: impossibile creare una nuova regola ordine fornitore con NUMBER_OF_SKUS tramite GraphQL"
description: Applica la patch ACSD-54626 per risolvere il problema di Adobe Commerce che impedisce al cliente di creare una nuova regola dell’ordine di acquisto ("createPurchaseOrderApprovalRule") con l’attributo "NUMBER_OF_SKUS" tramite GraphQL.
feature: Attributes, B2B, GraphQL, Purchase Orders
role: Admin, Developer
exl-id: 807f06e3-6708-4860-bf46-df4404124f27
source-git-commit: 35cd21581ee34a6213be42a79e159439b8856fb6
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-54626: impossibile creare una nuova regola ordine fornitore con NUMBER_OF_SKUS tramite GraphQL

La patch ACSD-54626 risolve il problema che impedisce al cliente di creare una nuova regola dell&#39;ordine di acquisto (`createPurchaseOrderApprovalRule`) con l&#39;attributo `NUMBER_OF_SKUS` tramite GraphQL. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.42. L’ID della patch è ACSD-54626. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il cliente non può creare una nuova regola ordine fornitore (`createPurchaseOrderApprovalRule`) con l&#39;attributo `NUMBER_OF_SKUS` tramite GraphQL.

<u>Prerequisiti</u>:

Installare e abilitare i moduli B2B di Adobe Commerce.

<u>Passaggi da riprodurre</u>:

1. Abilita le regole aziendali e di acquisto B2B.
1. Crea una società con regole di acquisto abilitate.
1. Esegui la seguente query GraphQL:

   ```
   mutation CreatePurchaseRule {
       createPurchaseOrderApprovalRule(
           input: {
               name: "Test Rule"
               description: "description"
               applies_to: "MQ=="
               status: ENABLED
               approvers: "MQ=="
               condition: {
                   attribute: NUMBER_OF_SKUS
                   operator: MORE_THAN
                   quantity: 10
               }
           }
       ) {
           uid
           name
           __typename
       }
   }
   ```

<u>Risultati previsti</u>:

Viene creata una regola di acquisto.

<u>Risultati effettivi</u>:

Viene generato il seguente errore:

```
{
    "errors": [
        {
            "message": "Required data is missing from a rule condition.",
            "locations": [
                {
                    "line": 2,
                    "column": 3
                }
            ],
            "path": [
                "createPurchaseOrderApprovalRule"
            ],
            "extensions": {
                "category": "graphql-input"
            }
        }
    ],
    "data": {
        "createPurchaseOrderApprovalRule": null
    }
}
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
