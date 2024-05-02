---
title: "ACSD-47292: i prodotti in bundle esauriti non sono disponibili nella risposta GraphQL"
description: Applica la patch ACSD-47292 per risolvere il problema di Adobe Commerce per cui i prodotti in bundle esauriti non sono disponibili nella risposta di GraphQL anche se "show out-of-stock products" (Mostra prodotti esauriti) è impostato su Sì.
exl-id: 377dc62f-d1cd-4292-b25d-53c498b772a9
feature: Admin Workspace, Categories, GraphQL, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# ACSD-47292: i prodotti in bundle esauriti non sono disponibili nella risposta di GraphQL

La patch ACSD-47292 risolve il problema che non consente ai prodotti in bundle esauriti di essere inclusi nella risposta di GraphQL anche se [!UICONTROL Display Out-of-Stock Products] è impostato su *[!UICONTROL Yes]*. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25. L’ID della patch è ACSD-47292. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I prodotti in bundle esauriti non sono disponibili nella risposta di GraphQL anche se [!UICONTROL Display Out-of-Stock Products] è impostato su *[!UICONTROL Yes]*.

<u>Passaggi da riprodurre</u>:

1. Vai a Amministrazione di Adobe Commerce > **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** e imposta [!UICONTROL Display Out-of-Stock Products] a *[!UICONTROL Yes]*.
1. Crea due prodotti semplici, s1 e s2.
1. Rendere s1 esaurito e non visibile singolarmente e s2 in magazzino e non visibile singolarmente, quindi assegnarli a una categoria.
1. Crea un prodotto in bundle con almeno un prodotto opzione e assegna s1 e s2 a questa opzione (tipo di input &quot;RadioButton&quot;).
1. Salva il prodotto in bundle e assegnalo a una categoria.
1. Vai alla vetrina e apri questo prodotto in bundle. L’opzione esaurita s1 è disattivata ma visibile.
1. Invia una richiesta GraphQL:

```GraphQL
{
  categoryList(filters: { ids: { in: ["3"] } }) {
    id
    name
    products(pageSize: 8, sort: { position: ASC }) {
      total_count
      items {
        id
        sku
        name
        ... on BundleProduct {
          url_key
          items {
            title
            sku
            options {
              quantity
              position
              is_default
              product {
                id
                name
                sku
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

l’opzione del bundle s1 è elencata nella risposta di GraphQL da [!UICONTROL Display Out-of-Stock Products] è impostato su *[!UICONTROL Yes]* ed è visibile sulla vetrina.

<u>Risultati effettivi</u>:

l’opzione del bundle s1 non è elencata nella risposta di GraphQL.

```GraphQL
"items": [
                                {
                                    "title": "oo1",
                                    "sku": "bundle2",
                                    "options": [
                                        {
                                            "quantity": 1,
                                            "position": 2,
                                            "is_default": false,
                                            "product": {
                                                "id": 2,
                                                "name": "s2",
                                                "sku": "s2"
                                            }
                                        }
                                    ]
                                }
                            ]
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
