---
title: Nomi di gruppi di clienti, segmenti e informazioni sulle regole promozionali esposti tramite [!DNL GraphQL]
description: Questo articolo fornisce un hotfix per impedire l'esposizione di nomi di gruppi di clienti, segmenti di clienti e informazioni sulle regole promozionali tramite  [!DNL GraphQL].
feature: GraphQL
role: Admin, Developer
source-git-commit: f32085c80c9dbce513dad15ebf5f77a0e6398466
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---


# Nomi di gruppi di clienti, segmenti e informazioni sulle regole promozionali esposti tramite [!DNL GraphQL]

Questo articolo fornisce un hotfix per impedire l&#39;esposizione di nomi di gruppi di clienti, segmenti di clienti e informazioni sulle regole promozionali tramite [!DNL GraphQL]. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8-p1.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.8

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.8

## Problema

Per [!UICONTROL Storefront Personalization Drop-ins], sono state introdotte nuove mutazioni di [!DNL GraphQL] per visualizzare informazioni di base come nomi di gruppi di clienti, segmenti, carrello e regole di catalogo. Tuttavia, questo può esporre dati sensibili come i dettagli dell’offerta o i codici coupon, se inclusi nei nomi.

### Passaggi da riprodurre

#### Caso I: [!UICONTROL Catalog Rule]

1. Nella barra laterale *Admin*, passa a **[!UICONTROL Marketing]** > **[!UICONTROL Catalog Price Rule]** > **[!UICONTROL Add New Rule]**.
1. Definisci le condizioni della regola (ad esempio, attributo o categoria di prodotto).
1. Salva e applica la regola.
1. Assicurati che un prodotto soddisfi le condizioni della regola.
1. Eseguire la seguente query [!DNL GraphQL] per recuperare tutte le regole:

   ```
   query {
       allCatalogRules {
           name
       }
   }
   ```

1. Eseguire una query su un prodotto per verificare se la regola è applicabile:

   ```
   query {
       products(filter: { sku: { eq: "product-sku" } }) {
           items {
               name
               rules {
                   name
               }
           }
       }
   }
   ```

#### Caso II: [!UICONTROL Cart Rule]

1. Nella barra laterale *Admin*, passa a **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rule]** > **[!UICONTROL Add New Rule]**.
1. Imposta condizioni quali valore minimo del carrello e gruppo di clienti.
1. Salva e applica la regola.
1. Aggiungi prodotti al carrello per attivare la regola.
1. Utilizza [!DNL GraphQL] per verificare tutte le regole del carrello:

   ```
   query {
       allCartRules {
           name
       }
   }
   ```

1. Verifica se le regole vengono applicate al carrello attivo:

   ```
   query {
       cart(cart_id: "your-cart-id") {
           rules {
               name
           }
       }
   }
   ```

#### Caso III: [!UICONTROL Customer Group]

1. Nella barra laterale *Admin*, passa a **[!UICONTROL Customers]** > **[!UICONTROL Customer Groups]**.
1. Verifica l’esistenza dei gruppi previsti.
1. Utilizza [!DNL GraphQL] per recuperare tutti i gruppi:

   ```
   query {
       allCustomerGroups {
           name
       }
   }
   ```

1. Verifica il gruppo del cliente/ospite:

   ```
   query {
       customerGroup {
           name
       }
   }
   ```

#### Caso IV: [!UICONTROL Customer Segment] (solo per Adobe Commerce)

1. Nella barra laterale *Admin*, vai a **[!UICONTROL Customers]** > **[!UICONTROL Customer Segments]** → **[!UICONTROL Add Segment]**.
1. Definire le condizioni basate sul cliente (ad esempio, ordine, contenuto del carrello).
1. Assegnare l&#39;ambito applicabile: *[!UICONTROL Visitor]*, *[!UICONTROL Registered]* o entrambi.
1. Assicurati che le condizioni corrispondano a un cliente di prova.
1. Utilizza [!DNL GraphQL] per controllare tutti i segmenti:

   ```
   query {
       allCustomerSegments {
           name
           apply_to
       }
   }
   ```

1. Convalida i segmenti applicati a un carrello:

   ```
   query {
       customerSegments(cartId: "your-cart-id") {
           name
       }
   }
   ```

<u>Risultato previsto</u>:

I nomi dei gruppi di clienti, dei segmenti e delle informazioni sulle regole promozionali non vengono esposti tramite [!DNL GraphQL].

<u>Risultato effettivo</u>:

I nomi di gruppi di clienti, segmenti e informazioni sulle regole promozionali sono esposti tramite [!DNL GraphQL].

## Soluzione

Applica le patch allegate in base alla versione di Adobe Commerce:

* Per Adobe Commerce versione 2.4.8:

   * [LYNX-839_CE_2.4.8.patch](assets/LYNX-839_CE_2.4.8.patch.zip)
   * [LYNX-839_EE_2.4.8.patch](assets/LYNX-839_EE_2.4.8.patch.zip)

* Per [!DNL Magento] Apri Source versione 2.4.8:

   * [LYNX-839_CE_2.4.8.patch](assets/LYNX-839_CE_2.4.8.patch.zip)
