---
title: "ACSD-54660: nuovo ordinamento dell'attributo di input per ordinare gli ordini dei clienti in [!DNL GraphQL]"
description: Applica la patch ACSD-54660 per risolvere il problema di Adobe Commerce in cui è stato aggiunto un nuovo attributo di input "sort" per ordinare gli ordini dei clienti in [!DNL GraphQL] by "sort_field" e "sort_direction".
feature: GraphQL, Orders
role: Admin, Developer
exl-id: 29869139-e5e2-4b00-a090-e2c6673ff9ca
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 0%

---

# ACSD-54660: è stato aggiunto un nuovo ordinamento di attributi di input per ordinare gli ordini dei clienti in [!DNL GraphQL]

La patch ACSD-54660 risolve il problema relativo all&#39;aggiunta di un nuovo attributo di input `sort` per ordinare gli ordini cliente in [!DNL GraphQL] da parte di `sort_field` e `sort_direction`. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.39. L’ID della patch è ACSD-54660. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.5-p5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Nuovo attributo di input `sort` aggiunto per ordinare gli ordini cliente in [!DNL GraphQL] da `sort_field` e `sort_direction`.

<u>Passaggi da riprodurre</u>:

Eseguire query sugli ordini dei clienti utilizzando [!DNL GraphQL]:

```
  {
    customerOrders {
      items {
        order_number
        id
        created_at
        grand_total
        status
      }
    }
  }
```

<u>Risultati previsti</u>:

Questa patch aggiunge `sort` e `sort_direction` argomenti a `customer.orders`.

<u>Risultati effettivi</u>:

Impossibile ordinare gli ordini utilizzando [!DNL GraphQL].

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
