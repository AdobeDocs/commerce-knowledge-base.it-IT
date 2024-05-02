---
title: '"ACSD-54660: nuovo ordinamento dell’attributo di input per ordinare gli ordini dei clienti in [!DNL GraphQL]'''
description: Applica la patch ACSD-54660 per risolvere il problema di Adobe Commerce, in cui viene aggiunto un nuovo attributo di input "sort" per ordinare gli ordini dei clienti in [!DNL GraphQL] da "sort_field" e "sort_direction".
feature: GraphQL, Orders
role: Admin, Developer
exl-id: 29869139-e5e2-4b00-a090-e2c6673ff9ca
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 0%

---

# ACSD-54660: aggiunta del nuovo ordinamento degli attributi di input per ordinare gli ordini dei clienti in [!DNL GraphQL]

La patch ACSD-54660 risolve il problema relativo a un nuovo attributo di input `sort` aggiunto per ordinare gli ordini cliente in [!DNL GraphQL] da `sort_field` e `sort_direction`. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.39. L’ID della patch è ACSD-54660. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.5-p5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Nuovo attributo di input `sort` aggiunto per ordinare gli ordini cliente in [!DNL GraphQL] da `sort_field` e `sort_direction`.

<u>Passaggi da riprodurre</u>:

Eseguire una query sugli ordini dei clienti utilizzando [!DNL GraphQL]:

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

Questa patch aggiunge `sort` e `sort_direction` argomenti per `customer.orders`.

<u>Risultati effettivi</u>:

Non è possibile ordinare gli ordini utilizzando [!DNL GraphQL].

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
